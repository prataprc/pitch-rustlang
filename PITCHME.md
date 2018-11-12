@title[Rust language]

@snap[midpoint slide1 span-60]
<h1>Rust</h1>
The next generation systems language <br/> <br/>
@color[blue](C) @color[](genesis circa-1970) <br/>
@color[brown](Rust) @color[](genesis circa-2010) <br/>
@snapend


@snap[south-east author-box]
@fa[envelope](prataprc@gmail.com - R Pratap Chakravarthy) <br/>
@snapend

---

Abstract: Rust and C
====================

Rust happens to carry forward all the goodness of C and avoiding,
as much as possible, its pitfalls, corner-cases and legacy issues.
Rust maintains the C like philosophy through and through, to
enable programmers with small, but powerful set of features that can
inter-play with each other seamlessly, unlike C++ large collection
of features that stick out.

<style> table th, table td { text-align: center !important; } </style>

<table class="south-west">
  <tr class="fragment">
    <th style="color: blue;"> Feature </th> <th> C </th> <th> Rust </th>
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
  <tr class="fragment">
    <td> Memory safety </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
  </tr>
</table>

<table class="south-east">
  <tr class="fragment">
    <th style="color: blue;"> Feature </th> <th> C </th> <th> Rust </th>
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

---

Introduction
============

@ul[para]
- Rust is essentially a @color[blue](type system framework), with many features, that one might expect to be part of the language, can be implemented as library.
@ulend

@ul[para]
- The compilation unit of rust program is called a @color[blue](crate), where crates can be further organised as @color[blue](modules), in separate @color[blue](files) and @color[blue](directories).
@ulend

@ul[para]
- A single rust program, treated as a compilation unit, also called as a crate is made up of @color[blue](items) and @color[blue](attributes).
@ulend

@ul[para]
- An @color[blue](item) is a component of a crate that are organised withing the crate by a nested set of modules.
@ulend

@ul[para]
- An @color[blue](attribute) is free-form metadatum on an item, that can be used to control the compiler's interpretation of the item.
@ulend

+++

Hello world
===========

<br/>

```rust
fn main() {
	println!("hello world");
}
```

@[1](main function returns unit type **(\)**)
@[2](o/p: hello world)

+++

Hello world, another version
============================

<br/>

```rust
fn main() -> io::Result<()> {
	println!("hello world");
	Ok(());
}
```

@[1](main function returns **Result<(\),io::Error>**)
@[2](o/p: hello world)

+++

Executing as script
===================

Rust programs can be executed as a script.

```rust
#!/usr/bin/env rustx

fn main() {
    println!("Hello world!");
}
```

@[1](indicates that this rust program to be executed as a script)
@[4](o/p: Hello world!)

---

Keywords
========

Rust keywords are identifier tokens that have special meaning. Keywords can
generally be classified between:

@ul
* **control flow** - @color[gray](break continue if else fn return loop for while match)
* **data** - @color[gray](false true box const let mut move ref self static)
* **type** - @color[gray](enum Self type struct trait unsafe where union impl)
* **compiler** - @color[gray](crate extern mod pub super self use)
@ulend

---

Data keywords
=============

Keywords reserved for data, literals, and its semantics.

@ul
* **false, true** - boolean data.
* **box** - allocate memory in heap and copies value into it.
* **let** - irrefutable variable binding, used to declare local variables.
* **ref** - reference to value (similar to pointers, but safe to use).
* **mut** - denote data as mutable (by default data is immutable).
* **move** - move semantics ...
* **self** - method receiver, similar to [this][this] in C++.
* **const** - data to be used as constant values.
* **static** - lifetime denotes the entire lifepsan of a program.
@ulend

[this]: https://www.geeksforgeeks.org/this-pointer-in-c/

---

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
* **Self** - inside **impl** and **trait** denotes the implementing type
@ulend

---

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

---

Compiler keywords
=================

Keywords reserved for compiler action.

@ul
* **crate** - unit of rust program than can be built into binary or library
* **extern** - linkage with other crates
* **mod** - organise rust crate into files and directories
* **pub** - specify user visible items in a crate
* **super** - parent module
* **self** - current module
* **use** - bringing items from other crates/modules into local scope.
@ulend

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

---

Identifier rules
================

* First character is a letter
* Remaining characters are @color[gray](_alphanumeric_) or @color[gray](_).

Regex: @color[gray]([A-Za-z][A-Za-z0-9_]*)

@snap[fragment mt20]
Identifier can also start with @color[gray](_) as first character,
in which case:
@snapend

@ul[mt20]
* If the identifier is named as @color[gray](\_), it is typically used to ignore a variable binding in pattern matching.
* Otherwise if the identifier starts with @color[gray](\_), will prevent compiler errors if such identifiers are left unused in its scope.
@ulend

@snap[fragment mt20]
Note that in the later case the move/copy semantics are still applicable,
while move/copy are not applicable in the former case.
@snapend

---

Comments
========

@ul
- Comments can either be **non-document comments**.
- Or, it can be **document comments**.
@ulend

@snap[fragment mt20]
**Non-document comments** in Rust code follow the general C++ style of line
@color[gray](//) and block @color[gray](/\* ... \*/) comment forms.
@snapend

@ul
- Nested block comments are supported.
- Non-doc comments are interpreted as a form of whitespace.
@ulend

@snap[fragment mt20]
Similar to non-document comments, **document comments** have two forms.
@snapend

@ul[mt20]
- Line doc comments @color[gray](///).
- Block doc comments @color[gray](/\*\* ... \*/).
- Document comments are essentially shortcut for @color[gray](#[doc="..."]).
- There is a variant to the two forms of document-comments
  -  Line comments of the form @color[gray](//!)
  -  Block comments of the form @color[gray](/*! ... */)
  - They are doc comments that apply to the parent of the comment, rather than the item that follows. That is, they are equivalent to writing @color[gray](#![doc="..."]) around the body of the comment.
  - @color[gray](//!) comments are usually used to document modules that occupy a source file.
@ulend

---

Whitespace
==========

List of whitespace token allowed in a rust program

|                                      |                              |
|--------------------------------------|------------------------------|
| U+0009 (horizontal tab, '\t')        | U+0085 (next line)           |
| U+000A (line feed, '\n')             | U+200E (left-to-right mark)  |
| U+000B (vertical tab)                | U+200F (right-to-left mark)  |
| U+000C (form feed)                   | U+2028 (line separator)      |
| U+000D (carriage return, '\r')       | U+2029 (paragraph separator) |
| U+0020 (space, ' ')                  |                              |

@ul[mt20]
- Rust is a "free-form" language.
- Rust program has identical meaning if each whitespace element.
- Non-document comments are treated as whitespace.
@ulend

---

Crates and Modules
==================

An example crate:

```rust
type Point = (i32,i32)

pub mod example_module {
	pub mod nested_module {
	}
}
```

@ul[mt20]
- The compilation model centers on artifacts called crates,
- Each compilation processes a single crate in source form, and produces an executable or library.
- A crate handles linking, versioning, distribution and runtime loading.
- A crate contains a root module, called anonymous module and a tree of nested module scopes.
- Rust source files always end with **.rs** extension.
- A crate that contains the **main()** function can be compile to an executable.
@ulend

@[3](nested module **example_module** that can be refered as <crate-name>::example_module)
@[4](nested module **example_module** that can be refered as <crate-name>::example_module::nested_module)

---

Inventory of Items
==================

<table class="items-left">
<tr><td class="text-brown"> type definitions </tr></td>
<tr><td class="text-brown"> struct definitions </tr></td>
<tr><td class="text-brown"> enumeration definitions </tr></td>
<tr><td class="text-brown"> union definitions </tr></td>
<tr><td class="text-green"> function definitions </tr></td>
<tr><td class="text-green"> trait definitions  </tr></td>
<tr><td class="text-green"> implementations  </tr></td>
</table>

<table class="items-right">
<tr><td class="text-blue"> module </tr></td>
<tr><td class="text-blue"> extern crate declaration  </tr></td>
<tr><td class="text-blue"> use declarations </tr></td>
<tr><td class="text-blue"> extern blocks </tr></td>
<tr><td class="text-gray"> constant items </tr></td>
<tr><td class="text-gray"> static items </tr></td>
</table>

---

Modules
=======

```rust
mod math {
    type Complex = (f64, f64);
    fn sin(f: f64) -> f64 {
        /* ... */
    }
    fn cos(f: f64) -> f64 {
        /* ... */
    }
    fn tan(f: f64) -> f64 {
        /* ... */
    }
}
```

@ul[mt20]
- A module is a container for zero or more items.
- Modules and types share the same namespace. This means in the same scope, types cannot have same name as the module.
- Items brought into scope with use also have this restriction.
- Every source file is a module, but not every module needs a source file.
@ulend

---

Modules, Files and Directories
==============================

As mentioned earlier a crate source can have its items organised in
module heirarchy. Extending on that, there is a nifty way to map module
name into file-name and directory name and there by organising code
in multiple files and directories:

<style> pre { width: 70% !important; } </style>

```rust
mod vec; // Load the `vec` module from `vec.rs`
mod util; // Load from util/mod.rs
mod thread {
    // Load the `local_data` module from `thread/local_data.rs`
    // or `thread/local_data/mod.rs`.
    mod local_data;
}
```

@snap[module-tree]
![TREE](assets/module-tree.png)
@snapend

@[1](A module without a body is loaded from an external file, by default with the same name as the module, plus the .rs extension.)
@[2](If module name is matching with a directory, then load from a default module called **mod.rs** under the matching directory path, typically every directory should contain a **mod.rs** that further declares each file under the directory as a module.)
@[6](When a directory does not have a mod.rs, then the parent module can include files under sub-directories by nested module declaration.)

---

Extern crates
=============

```rust
extern crate pcre;
extern crate std; // equivalent to: extern crate std as std;
extern crate std as ruststd; // linking to 'std' under another name
```

@ul[mt20]
- An extern crate declaration specifies a dependency on an external crate.
- The external crate is resolved to a specific **soname** at compile time, and a runtime linkage requirement to that soname is passed to the linker for loading at runtime.
- The soname is resolved at compile time by scanning the compiler's library path.
- When naming Rust crates, hyphens are disallowed. However, @color[blue](Cargo) packages may make use of them. In such case, Cargo will transparently replace @color[blue](-) with @color[blue](\_).
@ulend

@[1](The external crate **pcre** is bound into the declaring scope as **pcre** provided.)
@[2](Equivalent to - extern crate std as std;)
@[3](Possible to give different bound name.)

---

Use declaration
===============

```rust
use a::b::{c, d, e::f, g::h::i};
use a::b::{self, c, d::e};
use p::q::r as x;
use a::b::{self as ab, c as abc};
use a::b::*;
use a::b::{self as ab, c, d::{*, e::f}};

use std::option::Option::{Some, None};
use std::collections::hash_map::{self, HashMap};

fn main() {
    let x = vec![Some(1.0f64), None];
    let map1 = HashMap::new();
    let map2 = hash_map::HashMap::new();
}
```

@ul[mt20]
- A use declaration creates one or more local name bindings synonymous with some other path.
- Usually a use declaration is used to shorten the path required to refer to a module item.
- The conventions is to place these declarations at the top of modules and blocks.
- Note that, use declarations do not declare linkage dependancy with external crates.
@ulend

@[1](Simultaneously binding a list of paths with a common prefix, using the glob-like brace syntax.)
@[2](Simultaneously binding a list of paths with a common prefix and their common parent module, using the self keyword.)
@[3](Rebinding the target name as a new local name.)
@[4](Rebinding with glob-like syntax.)
@[5](Binding all paths matching a given prefix, using the asterisk wildcard syntax.)
@[6](Nesting groups of the previous features multiple times.)
@[12](Equivalent to 'vec![std::option::Option::Some(1.0f64), std::option::Option::None];')
@[13-14](Both `hash_map` and `HashMap` are in scope.)

---

Use: visibility and re-export
===============================

```rust
mod quux {
    pub use quux::foo::{bar, baz};

    pub mod foo {
        pub fn bar() { }
        pub fn baz() { }
    }
}
```

@ul[mt20]
- Like items, use declarations are private to the containing module, by default.
- Also like items, a use declaration can be public, if qualified by the **pub** keyword.
- Such a use declaration serves to re-export a name.
- A public use declaration can therefore redirect some public name to a different target definition.
- As a curious case, a definition with a private canonical path, inside a different module, can be re-exported as public item.
- If a sequence of use redirections form a cycle or cannot be resolved unambiguously, they represent a compile-time error.
- The general convention is to have top-level module declarations at the crate root, so that direct usage of the declared modules is possible within use items.
@ulend

@[2](Note that the paths contained in use items are relative to the crate root. So, the use refers to quux::foo::{bar, baz}, and not simply to foo::{bar, baz}.)

+++

Use declaration: Example
========================

```rust
use foo::baz::foobaz;    // good: foo is at the root of the crate
mod foo {
    mod example {
        pub mod iter {}
    }
    use foo::example::iter; // good: foo is at crate root
    use example::iter;      // bad:  example is not at the crate root
    use self::baz::foobaz;  // good: self refers to module 'foo'
    use foo::bar::foobar;   // good: foo is at crate root
    pub mod bar {
        pub fn foobar() { }
    }
    pub mod baz {
        use super::bar::foobar; // good: super refers to module 'foo'
        pub fn foobaz() { }
    }
}
```
@[1](good: foo is at the root of the crate.)
@[6](good: foo is at crate root.)
@[7](bad:  example is not at the crate root.)
@[8](good: self refers to module **foo**.)
@[9](good: foo is at crate root.)
@[14](good: super refers to module **foo**.)

---

Inventory of types
==================

Primitive types:

@ul
- **Boolean type**
- **Integer machine types - u8, u16, u32, u64, u128, i8, i16, i32, i64, i128**
- **Floating point - f32, f64**
- **Machine dependant integer types - isize, usize**
- **Textual types - char, str**
- **Never type !**
@ulend

@snap[mt20 fragment]
Complex types:
@snapend

@ul[mt20]
- **Structural type**
- **Tuple type**
- **Array type**
- **Slice type**
- **Function pointer**
- **Reference**
- **Pointer**
@ulend

---

Literals
========

@ul
- **Character** and **String** literals.

---

Literals: Character and Strings
===============================

|				   | Example	| Characters	| Escapes
|---------------   |------------|---------------|-----------------------
| Character		   | 'H'		| All Unicode	| Quote & ASCII & Unicode
| String		   | "hello"	| All Unicode	| Quote & ASCII & Unicode
| Raw			   | r#"hello"#	| All Unicode	| N/A
| Byte			   | b'H'		| All ASCII		| Quote & Byte
| Byte string	   | b"hello"	| All ASCII		| Quote & Byte
| Raw byte string  | br#"hello"#| All ASCII		| N/A

@ul[mt20]
- ASCII escapes are **\n**, **\r**, **\t**, **\\\\**, **\0**, finally any 7-bit character code (upto 0x7F) can be escaped as **\x..**
- Byte escapes are **\n**, **\r**, **\t**, **\\\\**, **\0**, finally any 8-bit character code can be escaped as **\x..**
- Unicode escapes are **\u{xxxxxx}** for 24-bit unicode character code.
- Quote escapes are **\'** and **\"**.
@ulend

---

Literals: Numbers
=================

| Type 			  | Example		| Exponentiation| Suffixes
|-----------------|-------------|---------------|-----------------------
| Decimal integer | 98_222		| N/A			| Integer suffixes
| Hex integer	  | 0xff		| N/A			| Integer suffixes
| Octal integer	  | 0o77		| N/A			| Integer suffixes
| Binary integer  | 0b1111_0000	| N/A			| Integer suffixes
| Floating-point  | 123.0E+77	| Optional		| Floating-point

@ul[mt20]
- All number literals allow **_ **as a visual separator: __1_234.0E+18f64__
- Integer suffixes - u8, i8, u16, i16, u32, i32, u64, i64, u128, i128, usize, isize
- Floating point suffixes - f32, f64
- By default integers are infered as **i32**.
- By default float is infered as **f32**.
@ulend

---

Literals: Boolean
=================

Tokens **true** and **false** are treated as boolean literal to be used
as boolean-true and boolean-false respectively.

---

Literals: Lifetimes and loop-labels
===================================

---

Operators
=========

Data operators:

@ul
* Arithmetic operators - ** +  - \* / % **
* Bitwise operators, ** >> << & | ^ ! **
* Assignment operator, ** = **
* Logical operator, ** & | ^ ! && || **
* Comparison operator, ** == != < <= > >=  **
* Assignment operator can be combined with arithmetic and bitwise operators
@snapend

@ulend

@snap[fragment mt20]
Other operators:
@snapend

@ul
* **@** Subpattern binding
* **_** Placeholder patterns, Inferred-types
* **.** Field-access, Tuple-index
* **..** Range, Struct-Expression, Wildcard-Patterns
* **...** Variadic-functions
* **..=** Inclusive-range
* **, :** used as separator in various places
* **;** Statement-terminator, Item-terminator, Array-type
* **::** Path-separator
* **->** Function-return, Closure-return
* **#** Attributes
* **$** Macros
* **?** Question-mark-operator, Questionably sized
@ulend

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

Path
====

```rust
x;
x::y::z;
type T = HashMap<i32,String>; // Type arguments used in a type expression
let x  = id::<i32>(10);       // Type arguments used in a call expression
```

@snap[fragment mt20]
A path is a sequence of one or more path components logically separated
by a namespace qualifier <b>::</b>
@snapend

@ul[mt20]
- If a path consists of only one component, it refers to either an item or a variable in a local control scope.
- If a path has multiple components, it always refers to an item.
- A path component is usually an identifier.
@ulend

@snap[fragment mt20]
The meaning of how a path is resolved can be changed with various <b>leading qualifiers</b>.
@snapend

@ul[mt20]
- **::** paths starting with <em>::</em> shall be resolved from crate root.
- **super** paths starting with <em>super</em> begin resolution relative to the parent module.
- **self** paths starting with <em>self</em> begin resolution relative to the current module.
@ulend


@[1](path refers a local variable.)
@[2](path refers to an item **z** in a //module// or //type// or //Enumeration// or //trait// **x** and **y**.)
@[3](path refer to a type **HashMap** parametrised over //i32// and //String//.)
@[4](Sometimes a path component might be of the form **<...>** to disabmbiguate the type or trait being refered to.)

+++

Path Resolution
===============

```rust
mod b {
    pub fn foo() {
        ::a::foo();
        super::a::foo();
    }
	fn bar() {
		self::foo();
	}
}
```

@[3](call a's foo function, resolving from crate root)
@[4](call a's foo function, resolving using super)
@[7](call a's foo function, resolving using self)

+++

Path Example
============

```rust
extern crate rand;
use std::option::Option::{Some, None};
type Point = (i32, i32);
enum Message {
	Put,
	Get,
}
union Union;
const BIT1: u32 = 1 << 0;
static mut LEVELS: u32 = 0;

mod a {
    pub fn foo() {}
    pub struct Struct;
    pub trait Trait {
        fn f(&self);
    }
    impl Trait for Struct {
        fn f(&self) {} // <::a::Struct as ::a::Trait>::f
    }
    impl Struct {
        fn g(&self) {} // <::a::Struct>::g
    }
}
```

@[1](extern-crate canonical path - ::rand)
@[2](use declaration don't have canonical path)
@[3](type canonical path - ::Point)
@[4](enum canonical path - ::Message)
@[5](enum variant canonical path - ::Message::Put)
@[8](union canonical path - ::Union)
@[9](constant canonical path - ::BIT1)
@[10](static canonical path - ::LEVELS)
@[12](module canonical path - ::a)
@[13](function canonical path - ::a::foo)
@[14](struct canonical path - ::a::Struct)
@[15](trait canonical path - ::a::Trait)
@[16](method canonical path - ::a::Trait::f)
@[18](implementation don't have canonical path)
@[19](method disambiguation - <::a::Struct as ::a::Trait>::f)
@[22](method canonical path - <::a::Struct>::g)

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

---

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

---

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

---

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

---

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

Move semantics
Pattern matching
Refutable bindings and Irrefutable bindings

Parametric Types
Enumerated types
Lifetimes - static, stack, heap
Safety
Mono-morphisation
Macro
Closure

Crate, Modules, files and directories.

Attributes

#[doc="..."]
#![crate_name = "projx"] // Specify the crate name.
#![crate_type = "lib"] // Specify the type of output artifact.
#![warn(non_camel_case_types)] // Turn on a warning.
#[path = "thread_files"]
mod thread {
    // Load the `local_data` module from `thread_files/tls.rs`
    #[path = "tls.rs"]
    mod local_data;
}

What are the limitations of user defined types ?
Are there any special significance attached to main.rs ?
Are there any special significance attached to lib.rs ?

---

traits

Auto-traits :
Core-traits :

Termination
