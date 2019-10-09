Casting
=======

Casting boolean to integer, true->1, false->0

What does it mean to mark a trait as unsafe or auto ?
EG: pub unsafe auto trait Send { }

Blog about trait pollution, example with `rdms`.

Extracting bound-limits from RangeBounds
========================================

```
let start = match within.start_bound() {
    Bound::Included(x) => Bound::Included(*x),
    Bound::Excluded(x) => Bound::Excluded(*x),
    Bound::Unbounded => Bound::Unbounded,
};
```

Would be nice to have an API defined by ``RangeBounds`` trait
to return a tuple of (upper, lower) bounds.

Doctests that require non-default feature
=========================================

```
/// Documentation relevant to all users.
/// Documentation relevant to all users.
/// Documentation relevant to all users.
///
/// Paragraph that mentions the feature.
#[cfg_attr(feature = "feature", doc = r##"
Paragraph that only appears when feature is enabled.

```
// doctest that only exists when the feature is enabled
```
"##)]
```


Feature gating testcases
========================

Sometimes we need to run a subset of assorted unit-test-functions
with no particular pattern. (for executing test functions with similar
names there is a separate slide).

In the following example we are defining three features in Cargo.toml
file like:

```toml
[features]
low_level = []
mid_level = []
high_level = []
```

and in our unit-test function we attribute them with each features.

```
#[cfg(feature = "low_level")]
fn test_one() {
}

#[cfg(feature = "mid_level")]
fn test_two() {
}

#[cfg(feature = "high_level")]
fn test_three() {
}
```

Now with the above setup, we can invoke ``cargo test`` like:

```
cargo test --features=low_level
```

will execute only those unit-test functions that are feature gated with
``low_level``.

```
cargo test --features=low_level && cargo test --features=mid_level && cargo test --features=high_level
```

will execute ``low-level`` function, failing which remaining test
cases are skipped. ``mid_level`` functions shall be executed only after
``low_level`` have passed and ``high_level`` functions shall be executed
only after ``mid_level`` functions have passed.

Executing testcases with similar names
======================================

```
cargo test serialize
```

Above command will execute all unit-test-functions whose function
name contain ``serialize``.

```
cargo test llrb_test::
```

Above command will execute all unit-test-functions under file
``llrb_test.rs``.


Unsizing and Coerced Unsizing
=============================

How to convert ``Rc<RefCell<Dog>>`` to ``Rc<RefCell<dyn AnimalT>>`` ?

```
use std::rc::Rc;
use std::cell::RefCell;

struct Dog(i32);

trait Animal {}

impl Animal for Dog {}

fn main() {
  let dog: Rc<RefCell<Dog>> = Rc::new(Dog(0).into());
  let dog2 = Rc::clone(&dog);
  let x: Rc<RefCell<dyn Animal>> = dog2;
}
```

Unsize is used to mark types which can be coerced to DSTs if behind
pointers. It is implemented automatically by the compiler.

+++

Unsize implementation
=====================

* [T; N] is Unsize<[T]>
* T is ``Unsize<Trait>`` when T: Trait
* ``Foo<..., T, ...>`` is ``Unsize<Foo<..., U, ...>>`` if:
  * T: ``Unsize<U>``
  * Foo is a struct
  * Only the last field of Foo has a type involving T
  * T is not part of the type of any other fields
  * ``Bar<T>: Unsize<Bar<U>>``, if the last field of Foo has type ``Bar<T>``

Modules and path names
======================

Module path           | Filesystem path | File contents
--------------------------------------------------------
crate	              | lib.rs	        | mod util;
crate::util	          | util.rs	        | mod config;
crate::util           | util/mod.rs     | mod config;
crate::util::config	  | util/config.rs

Note it is not allowed to have both util.rs and util/mod.rs.

Making both binary and cdylib from one package
==============================================

```
[lib]
crate-type = ["cdylib", "rlib"]
```

selectively compile functions for testing
=========================================

Test functions are normally attributed with `#[test]` and/or
`#[cfg(test)]`. Similarly if there are any functions or methods
that are going to be used only by test-cases, such functions or
methods can be attributed with `#[cfg(test)]`.

```
impl Mvcc {
    #[cfg(test)]
    pub(crate) fn mvccroot_ref(&self) -> &MvccRoot<K, V> {
        unsafe { self.snapshot.value.load(Relaxed).as_ref().unwrap() }
    }
}
```

In above case method `mvccroot_ref` is used only by the test
cases, hence we don't need it as part of the development build.

Setting deep value within structs
=================================

```
struct Foo {
    a: Option<Bar>
}

struct Bar {
    b: Baz
}

struct Baz {
    c: Option<u32>
}

fn set_deep_value(mut example:Foo) -> Option<Foo> {
    example.a.as_mut()?.b.c = Some(42);
    Some(example)
}
```


Destructing from reference to mutable copy
==========================================

```
fn ref_to_immutable_copy(&x: &i32) {
    // scope takes immutable ownership of value, by copy.
    println!("x = {}", x);
}

fn mutable_ref(x: &mut i32) {
     // scope takes a mutable reference via x.
    *x = 20;
    println!("x = {}", *x);
}

fn mut_ref_to_mut_copy(&mut mut x: &mut i32) {
    // scope takes a mutable ownership of value, by copy
    x = 20;
    println!("x = {}", x);
}
```

Ownned heap to shared reference
===============================

Both Box<T> and &T are nothing but a pointer reference. That being
said, the former case owns the reference while the later case holds
on to a shared reference. Here is a neat trick to convert between
the two.

From Box<T> to &T
```
let a = Box::new(10);
let b = &*a;
```

From &T to Box<T>
```
fn myfunc(arg: &i32) -> Box<T> {
    // Note that we are creating a duplicate ownership
    // for the value pointed by arg here. Make sure that
    // one of them leaks.
    unsafe{ Box::from_raw(arg as *const T as *mut T) }
}

fn main() {
    let a = Box::new(10);
    let b = myfunc(&a);
    Box::leak(b); // we are leaking b here
}
```


Avoiding pollution of constraints
=================================

When parametrising data structures with types, especially
those that are algorithmically intensive, we quickly find
that plenty of contraints, aka trait bounds, gets added to
type parameters.

For EG:

```
struct Llrb<K,V>
where
    K: Clone + Ord,
    V: Clone,
{
}
```

is Llrb tree used for indexing {Key, Value} pairs, where
key and value types are parameterised. One of the API that
gets exposed as part of the type implementation is the
validate() API, which ensures that data-set is in sane
condition. Failing which it needs to capture the erroring
entry that might involve a `Debug` constraint on K parameter.

Now a situation arises where K type needs to be bounded by
Debug trait. But we don't want this to be part of Llrb type
signature. To achieve this:

```
impl<K,V> for Llrb<K,V>
where
    K: Clone + Ord + Debug,
    V: Clone,
{
    fn validate(..) -> .. {}
{
```

Just club the functions that require a common set of trait
bounds into a single implementation and add those trait bounds
only for that implementation.

```
use std::fmt::Debug;

#[derive(Clone)]
struct S(i32);

struct Mytype<K>
where
    K: Clone,
{
    a: K,
}

impl<K> Mytype<K>
where
    K: Clone,
{
    fn new(k: K) -> Mytype<K> {
        Mytype { a: k }
    }

    fn value(&self) -> i32 {
        10
    }
}

impl<K> Mytype<K>
where
    K: Clone + Debug,
{
    fn validate(&self) -> String {
        format!("{:?}", self.a)
    }
}

fn main() {
    let a = Mytype::new(S(10));
    println!("{}", a.value());
}
```

Use Option instead of Default
=============================

When designing the APIs with type-parameters, it is tempting
to bound them with a Default constraint. In most cases such
need arises because in some context, we may want to initialize
the parametrised type with a default value.

In such cases, use Option<T> and initialize with None, instead
of contraining T: with Default.

Pipelining Option
=================

Sometimes, we would want to tranform the output `Option<T>` to
`Option<U>`, so on and so forth. One sleek way to do that is:

```
fn sq(x: u32) -> Option<u32> { Some(x * x) }
fn nope(_: u32) -> Option<u32> { None }

assert_eq!(Some(2).and_then(sq).and_then(sq), Some(16));
assert_eq!(Some(2).and_then(sq).and_then(nope), None);
assert_eq!(Some(2).and_then(nope).and_then(sq), None);
assert_eq!(None.and_then(sq).and_then(sq), None);
```

`and_then` return None if the option is None, otherwise calls
`f` with the wrapped value and returns the result.

Some languages call this operation `flatmap`.


API convention for converting type and references
=================================================

Conversions should be provided as methods, with names prefixed as follows:

Prefix      | Cost       | Ownership
--------------------------------------------------------------
as\_        | Free       | borrowed -> borrowed
--------------------------------------------------------------
to\_        | Expensive  | borrowed -> borrowed
            |            | borrowed -> owned (non-Copy types)
            |            | owned -> owned (Copy types)
--------------------------------------------------------------
into\_      | Variable   | owned -> owned (non-Copy types)


panic on lossy casting
======================

```
Executing an as expression casts the value on the left-hand
side to the type on the right-hand side.
```

For more information:
https://doc.rust-lang.org/reference/expressions/operator-expr.html?highlight=cast#type-cast-expressions

Using `as` expression to cast from one type to another might lead
to lossy conversion. If such behaviour is not desired, TryInto trait
can be used. EG:

```
let x: i32 = 10;
let y: u8 = x.try_into().unwrap(); // if we are sure that  0 <= x < 256
match x.try_into() {
    Ok(y) => ...
    Err(err) => ...
}
```

AsRef, Borrow for flexible APIs
===============================

When designing API rust has few options to provide maximum flexibility
for API users. A best example can be found with get() and range()
method from std lib's BTreeMap collection:

```
pub fn get<Q>(&self, key: &Q) -> Option<&V>
where
    K: Borrow<Q>,
    Q: Ord + ?Sized,
```

and,

```
pub fn range<T, R>(&self, range: R) -> Range<K, V>
where
    K: Borrow<T>,
    R: RangeBounds<T>,
    T: Ord + ?Sized,
```

In the former case, `key` is anything that can be borrowed from `K`.
In the later case, `range` can be anything that implements
RangeBounds, which includes `..`, `start..`, `start..end`,
`start..=end`, `..end`, `..=end` over `T` or `&T` and, for
two-element tuples like: (T, T) (&T, &T).

`AsRef` bounds can be used instead of Borrow. The difference
between AsRef and Borrow being that.

* Unlike AsRef, Borrow has a blanket impl for any T, and can be
  used to accept either a reference or a value.
* Borrow also requires that Hash, Eq and Ord for borrowed value
  are equivalent to those of the owned value. For this reason,
  if you want to borrow only a single field of a struct you can
  implement AsRef, but not Borrow.
* AsRef auto-dereferences if the inner type is a reference or a
  mutable reference (e.g.: foo.as_ref() will work the same if foo
  has type &mut Foo or &&mut Foo)

clone on steriod, Borrow and ToOwned
====================================

Some types make it possible to go from borrowed to owned, usually
by implementing the Clone trait. But Clone works only for going from
&T to T. The ToOwned trait generalizes Clone to construct owned data
from any borrow of a given type.

To borrow `&str` from `String`:

```
impl Borrow<str> for String {
    fn borrow(&self) -> &str;
}
```

To clone `String` from `&str`:

```
impl ToOwned for str {
    type Owned = String;
    fn to_owned(&self) -> String;
}
```

casting c-like enumeration
==========================

Enum types can be used similar to C enums.

```
enum Color {
    Red = 1,
    Black = 2,
    White = 3,
}
```

And for performance reasons, like using the enum value in lookup tables,
might require to translate enum to number. Try this:

```
#[derive(Copy,Clone)]
enum Color {
    Red = 1,
    Black = 2,
    White = 3,
}

// else where
let c = Color::Red;
lookup_table[c as usize];
```

type annotation, partial inference
==================================

Type annotation is required for situations like:

```
let x = "hello".chars().rev().collect();
```

which can be fixed with:

```
let x: Vec<char> = "hello".chars().rev().collect();
```

It is not necessary to annotate the full type. Once the ambiguity
is resolved, the compiler can infer the rest:

```
let x: Vec<_> = "hello".chars().rev().collect();
```

rustdoc: hyper links for public items
=====================================

```rust
/// Depth calculates minimum, maximum, average and percentile
/// of leaf-node depths in the [Llrb] tree.
```

Above documentation refers to a type, Llrb, a crate level public item.
Instead of using [Llrb], try using [crate::Llrb].

Alternately,

```rust
#[allow(unused_import)]
use crate::Llrb;

/// Depth calculates minimum, maximum, average and percentile
/// of leaf-node depths in the [Llrb] tree.
```

Import the item into local scope, and if the item is imported
only for hyper-linking items for rustdoc, attribute the import
as `unused_import`


rustdoc: highlight cross links
==============================

```rust
/// Depth calculates minimum, maximum, average and percentile
/// of leaf-node depths in the [Llrb] tree.
```

In above documentation by changing [Llrb] to [`Llrb`] we can highlight
the hyper-link to add some emphasis.
