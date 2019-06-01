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
