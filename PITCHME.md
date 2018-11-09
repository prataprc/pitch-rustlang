@title[Rust language]

@snap[midpoint slide1 span-60]
<h1>Rust</h1>
@size[80%](The next generation systems language) <br/> <br/>
@size[80%](@color[blue](C) @color[](genesis circa-1970)) <br/>
@size[80%](@color[brown](Rust) @color[](genesis circa-2010)) <br/>
@snapend


@snap[south-east author-box]
@fa[envelope](prataprc@gmail.com - R Pratap Chakravarthy) <br/>
@snapend

---

Introduction
============

@ul[para]
- Rust is essentially a @color[blue](type system framework), with many features, that one might expect to be part of the language, can be implemented as library.
@ulend

@ul[para]
- The compilation unit of rust program is called a @color[blue](crate), where crates can be further organised as @color[blue](modules), in separate @color[blue](files) and @color[blue](directories).
@ulend

---

Rust Vs C
==========
<style> table th, table td { text-align: center !important; } </style>
<style> table { font-size: 90% } </style>

@snap[west span-50]
<table>
  <tr class="fragment">
    <th style="color: blue;"> Compared </th> <th> C </th> <th> Rust </th>
  </tr>
  <tr class="fragment">
    <td> Hardware access </td> <td class="text-blue"> Y </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Pointers </td> <td class="text-blue"> Y </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Link with C binary </td> <td class="text-blue"> Y </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Garbage collection </td> <td class="text-red"> N </td> <td class="text-red"> N </td>
  </tr>
  <tr class="fragment">
    <td> Zero Cost Abstraction </td> <td class="text-blue"> Y </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> LLVM Backend </td> <td class="text-blue"> Y </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Standard Library </td> <td class="text-blue"> Y </td> <td class="text-blue"> Y </td>
  </tr>
</table>
@snapend

@snap[east span-50]
<table>
  <tr class="fragment">
    <th style="color: blue;"> Advantage </th> <th> C </th> <th> Rust </th>
  </tr>
  <tr class="fragment">
    <td> Memory safety </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Type inference </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Parametric types </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Mono-morphisation </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Enumerated types </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Pattern matching </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Build and packaging </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Macro </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
  </tr>
  <tr class="fragment">
    <td> Closures </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
  </tr>
</table>
@snapend

---

Keywords
========

Rust keywords are identifier tokens that have special meaning. They can generally
be classified between:

* **control flow** - break, continue, if, else, fn, return, loop, for, while, match
* **data** - false, true, box, const, let, mut, move, ref, self, static
* **type** - enum, Self, type, struct, trait, unsafe, where, union, impl
* **compiler** - crate, extern, mod, pub, super, self, use

+++

Control keywords
================

Keywords reserved for control flow of a rust program.

@ul
* **if, else** - predicate based execution branching.
* **loop, for, while** - iteration blocks.
* **break** - exit loops.
* **continue** - skip to next iteration.
* **match** - refutable pattern matching on data shapes and values.
* **fn** - function definition.
* **return** - early return from a function block.
@ulend

+++

Data keywords
=============

Keywords reserved for data, literals, and its semantics.

@ul
* **false, true** - boolean data.
* **box** - to allocate memory in heap and copies value into it.
* **let** - irrefutable variable binding, used to declare local variables.
* **ref** - reference to value (similar to pointers, but safe to use).
* **mut** - denote data as mutable (by default data is immutable).
* **move** - move semantics ...
* **self** - method receiver.
* **const** - data to be used as constant values.
* **static** - live for the entire lifetime of the program.
@ulend

+++

Type keywords
=============

Keywords reserved for rust type system.

@ul
* **type** - create type aliases
* **struct** - heterogeneous collection of types, similar to tuples
* **union** - all items in a union share common storage space.
* **enum** - enumerated types, from value enumeration to type enumeration
* **trait** - define a collection of behaviours that can be implemented by types
* **impl** - implementing types and traits
* **where** - to declare constraints on types and traits
* **unsafe** - declare a type or block of code as unsafe
* **Self** - type of method receivers
@ulend

+++

Compiler keywords
=================

Keywords reserved for compiler action.

* **crate** - unit of rust program than can be built into binary or library
* **extern** - linkage with other crates
* **mod** - organise rust crate into files and directories
* **pub** - specify user visible items in a crate
* **super** - parent module
* **self** - current module
* **use** - bringing items from other crates/modules into local scope.

---

Identifiers
===========

Similar to symbols in C, used to name items in a rust program. Like,

@ul
- Type-name, can be a tuple, struct, union, alias.
- Field-name within struct and union
- Variant-name within enumeration
- Associated types
- Function-name
- Variable-name (local, constant, static)
- Trait-name
- Module-name
- Crate-name
@ulend

+++

Identifier rules
================

* First character is a letter
* Remaining characters are alphanumeric or @color[blue](_).

Regex: @color[blue]([A-Za-z][A-Za-z0-9_]*)

Identifier can also start with @color[blue](_) as first character,
in which case:

* If the identifier is named as @color[blue](_), it is typically
  used to ignore a variable binding in pattern matching.
* Otherwise if the identifier
 starts with @color[blue](_), will prevent compiler errors if such identifiers are left unused in its scope.

Note that in the later case the move/copy semantics are still applicable,
while move/copy are not applicable in the former case.

---

@title[types]

@snap[midpoint text-center]
<h1 style="text-align: center !important;">Types</h1>
<br/>
Every variable, item and value in Rust has a type. The type of a value defines
the interpretation of the memory holding it.
@snapend

---

Primitive types
===============

Some types are defined by the language, rather than as part of the
standard library, these are called primitive types.

@ul
- **Boolean type** bool with values @color[blue](true, false).
- **Integer machine types** unsigned word types @color[blue](u8, u16, u32, u64, u128), signed 2’s complement word types @color[blue](i8, i16, i32, i64, i128).
- **Floating point** machine types @color[blue](f32, f64).
- **Machine dependant integer types** with same number of bits as platform’s pointer type, used for indexing and pointer offset @color[blue](usize, isize).
- **Textual types** @color[blue](char, str). Char is [unicode scalar value](http://www.unicode.org/glossary/#unicode_scalar_value) and @color[blue]([char]) is effectively an UCS4/UTF-32 array. Str is dynamically sized type that represents [utf8](https://en.wikipedia.org/wiki/UTF-8) encode string.
- **Never type !**, expressions of type ! can be coerced into any other type.
@ulend

---

Complex types
=============

@ul
- Structural type
- Tuple type
- Array type
- Slice type
- Function pointer
- Reference
- Pointer
@ulend

---

Structural type
===============

A struct type is a heterogenous product of other types, called the **fields**
of the type.

Memory layout of a struct is undefined by default to allow for optimizations,
nevertheless it can be fixed using the **#[repr(...)]** attribute.

```rust
pub struct Point3d {
	pub x: i32;
	pub y: i32;
	transform: i64;
}

Point {x: 10.0, y: 20.0};
struct NothingInMe; // unit like struct
NothingInMe {} // expression;
TuplePoint(10.0, 20.0);
TuplePoint { 0: 10.0, 1: 20.0 };

let u = game::User {name: "Joe", age: 35, score: 100_000};
some_fn::<Cookie>(Cookie);

struct Point3d { x: x, y: y_value, z: z };
struct Point3d { x, y: y_value, z };

let base = Point3d {x: 1, y: 2, z: 3};
Point3d {y: 0, z: 10, .. base};

```

@[1-5](Struct declaration. Fields of a struct can be qualified by visibility modifier, here **x** and **y** are publicly visible items, but **transform** is private to struct)
@[7](In a struct expression, fields may be given in any order and the resulting struct value will always have the same memory layout.)
@[8-9](A unit-like struct type is like a struct type, except that it has no fields.)
@[16-17](STRUCT FIELD INIT SHORTHAND.)
@[19-20](SHORTHAND NOTATION FOR CONSTRUCTING PARTIALLY MODIFIED STRUCT.)

---

Enumerated types
================

```rust
enum Message {
	Quit,
	WriteString(String),
	Move{x: i32, y: i32},
}

let q = Message::Quit;
let w = Message::WriteString("Some string".to_string());
let m = Message::Move { x: 50, y: 200 };
```

@ul
- An enumerated type is a nominal, heterogeneous disjoint union type, denoted by the name of an enum item.
- An **enum item** declares both the type and a number of variants, each of which is independently named and each variant has the syntax of a **struct**, **tuple struct** or **unit-like struct**.
- Any enum value consumes as much memory as the largest variant for its corresponding enum type, as well as the size needed to store a discriminant.
@ulend

@[1-3](Declaring an enumerated type and its variants.)
@[6-8](Enumeration variants can be constructed similarly to structs, using a path to an enum variant instead of to a struct.)

---

Visibility and privacy
======================

@snap[fragment]
Visibility of an [item](...) in a rust program decides whether it can be
accessed outside its scope. Note that Rust's name resolution operates on
a global hierarchy of namespaces, where each level in the hierarchy can
be thought of as some item.
@snapend

@snap[fragment]
And each item can either be **private** or **public**. By default,
**everything in Rust is private**, with two exceptions:
@snapend

@ul
- Associated items in a @color[blue](pub trait) are public by default.
- Enum variants in a @color[blue](pub enum) are also public by default.
@ulend

@snap[fragment mt20]
To declare an item as public, it shall be prefixed with @color[blue](pub)
keyword. Public items can be thought of as being accessible to the outside
world.
@snapend

@snap[fragment mt20]
Subsequently, following two rules dictate the **visibility rule** in
accessing an item:
@snapend

@ul
- If an item is public, then it can be accessed externally from some module **m** if you can access all the item's parent modules from **m**.
- If an item is private, it may be accessed by the current module and its descendants.
@ulend

+++

Visibility case: helper functions
=================================

A crate needs a global available "helper module" to itself, but it
doesn't want to expose the helper module as a public API.

```rust
mod crate_helper_module {
    pub fn crate_helper() {}
    fn implementation_detail() {}
}
```

@[1](This module is private, meaning that no external crate can access this module. Because it is private at the root of this current crate, however, any module in the crate may access any publicly visible item in this module.)
@[2](This function can be used by anything in the current crate.)
@[3](This function *cannot* be used by anything else in the crate. It is not publicly visible outside of the `crate_helper_module`, so only this current module and its descendants may access it.)

+++

Visibility case: library APIs
=============================

A library developer needs to expose functionality to crates which link
against their library. As a consequence of the first case, this means
that anything which is usable externally must be pub from the root down
to the destination item.

```rust
pub fn public_api() {}

pub mod submodule {
    use crate_helper_module;

    pub fn my_method() {
        crate_helper_module::crate_helper();
    }

    fn my_implementation() {}
}
```

@[1](This function is "public to the root" meaning that it's available to external crates linking against this one.)
@[3](Similarly to 'public_api', this module is public so external crates may look inside of it.)
@[4](can use crate_helper_module which is invisible external to crate, note that to make use of a visible item in a scope, it must first be imported to the local scope using the **use** declaration.)
@[10](This function is hidden to any module which is not a descendant of `submodule`.)

+++

Visibility case: unit testing
=============================

When writing unit tests for a module, it's often a common idiom to have
an immediate child of the module to-be-tested named @color[blue](mod test).
This module could access any items of the parent module through the
second case, meaning that internal implementation details could also be
seamlessly tested from the child module.

```rust
pub mod submodule {
    use crate_helper_module;
    fn my_implementation() {}

	#[cfg(test)]
	mod test {

	#[test]
		fn test_my_implementation() {
			super::my_implementation();
		}
	}
}
```

@[10](Because this module is a descendant of `submodule`, it's allowed to access private items inside of `submodule` without a privacy violation.)

---

Visibility: fine grained
========================

<br/>

@snap[fragment]
In addition to public and private, Rust allow users to declare an item
as visible within a given scope. The rules for pub restrictions are as follows:
@snapend

@ul
* **pub(in path)** makes an item visible within the provided path. path must be a parent module of the item whose visibility is being declared.
* **pub(crate)** makes an item visible within the current crate.
* **pub(super)** makes an item visible to the parent module. This is equivalent to pub(in super).
* **pub(self)** makes an item visible to the current module. This is equivalent to pub(in self).
@ulend

+++

Visibility: Example
===================

```rust
pub mod outer_mod {
    pub mod inner_mod {
        pub(in outer_mod) fn outer_mod_visible_fn() {}
        pub(crate) fn crate_visible_fn() {}
        pub(super) fn super_mod_visible_fn() {
            inner_mod_visible_fn();
        }
        pub(self) fn inner_mod_visible_fn() {}
    }
    pub fn foo() {
        inner_mod::outer_mod_visible_fn();
        inner_mod::crate_visible_fn();
        inner_mod::super_mod_visible_fn();

        inner_mod::inner_mod_visible_fn();
    }
}

fn bar() {
    outer_mod::inner_mod::crate_visible_fn();
    outer_mod::inner_mod::super_mod_visible_fn();
    outer_mod::inner_mod::outer_mod_visible_fn();
    outer_mod::foo();

}
```

@[3](This function is visible within `outer_mod`.)
@[4](This function is visible to the entire crate.)
@[5](This function is visible within `outer_mod`.)
@[6](This function is visible since we're in the same `mod`.)
@[8](This function is visible.)
@[15](This function is no longer visible since we're outside of `inner_mod`. Error! `inner_mod_visible_fn` is private.)
@[20] (This function is still visible since we're in the same crate.)
@[21] (This function is no longer visible since we're outside of `outer_mod`. Error! `super_mod_visible_fn` is private.)
@[22] (This function is no longer visible since we're outside of `outer_mod`. Error! `outer_mod_visible_fn` is private.)

---

Visibility: Re-exporting
=======================

Rust's @color[blue](use) declaration can be used to import publicly
visible items from elsewhere into local scope. By using the @color[blue](pub)
specifier along with **use** declaration we can re-export the imported item
from the current scope.

```rust
pub use self::implementation::api;

mod implementation {
    pub mod api {
        pub fn f() {}
    }
}
```

@snap[fragment]
This means that any external crate referencing
@color[blue](implementation::api::f) would receive a privacy violation,
while the path @color[blue](api::f) would be allowed.

---

Dynamically sized type
======================

@ul
- Types that don’t have its size known at compile type
- They are not first-class types
- Always instantiated behind a pointer type like &str.
@ulend

@snap[fragment]
Examples:
@snap

@ul
- **str**, pointing into a valid utf8 string/sub-string, of unknown size.
- **[T]**, aka slice, pointing into a array of element type T.
- **Trait objects**
@ulend

---

Coersion rules
==============

**! -> any type**

---

Operators and traits
====================

And, Or, Xor, Not
BitAnd, BitOr

---

Crate, Modules, files and directories.
Move semantics
What are the limitations of user defined types ?
How to escape markdown syntax ?
