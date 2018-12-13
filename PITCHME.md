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

What we can do with Rust ?
==========================

<table class="size-50">
<tr><th> Doing what    </th> <th> Rust     </th> <th> C        </th> <th> Python   </th> <th> Java     </th> <th> Golang   </th> <th> C#       </th> <th> Swift    </th> <th> js       </th> </tr>
<tr class="fragment"><td> Boot loader   </td> <td> &#10004; </td> <td> &#10004; </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> </tr>
<tr class="fragment"><td> Firmware      </td> <td> &#10004; </td> <td> &#10004; </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> </tr>
<tr class="fragment"><td> Kernel        </td> <td> &#10004; </td> <td> &#10004; </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> </tr>
<tr class="fragment"><td> Script        </td> <td> &#10004; </td> <td>          </td> <td> &#10004; </td> <td>          </td> <td> &#10004; </td> <td> &#10004; </td> <td>          </td> <td> &#10004; </td> </tr>
<tr class="fragment"><td> Middleware    </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> </tr>
<tr class="fragment"><td> Algorithms    </td> <td> &#10004; </td> <td> &#10004; </td> <td>          </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> </tr>
<tr class="fragment"><td> Database      </td> <td> &#10004; </td> <td> &#10004; </td> <td>          </td> <td> &#10004; </td> <td> &#10004; </td> <td>          </td> <td> &#10004; </td> <td>          </td> </tr>
<tr class="fragment"><td> Web-stack     </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> </tr>
<tr class="fragment"><td> Browser <span style="color: gray;">\*</span> </td> <td> &#10004; </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> <td>          </td> <td> &#10004; </td> </tr>
<tr class="fragment"><td> Windows       </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td>          </td> <td> &#10004; </td> </tr>
<tr class="fragment"><td> OSX           </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td> &#10004; </td> <td>          </td> <td> &#10004; </td> <td> &#10004; </td> </tr>
<tr class="fragment"><td> Android / iOS <span style="color: gray;">\*</span> </td> <td> &#10004; </td> <td>          </td> <td>          </td> <td> &#10004; </td> <td> &#10004; </td> <td>          </td> <td> &#10004; </td> <td>          </td> </tr>
</table>

@snap[size-50 text-gray south fragment]
<span style="color: gray;">\*</span> encouraging work in progress
@snapend

---

Rust and C
==========

@snap[mt20 size-80 fragment]
Rust maintains C like philosophy through and through, to enable
programmers with small, but powerful set of features that can inter-play
with each other seamlessly.
@snapend

<style> table th, table td { text-align: center !important; } </style>

<table class="size-60 south-west">
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

<table class="size-60 south-east">
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
    <td> Macros </td> <td class="text-red"> N </td> <td class="text-blue"> Y </td>
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
- An @color[blue](item) is a component of a crate that are organised within the crate by a @color[blue](nested set of modules).
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

@[1](main function returns unit type - **(\)**)
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

@[1](main function returns - **Result<(\),io::Error>**)
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

@[1](Indicates that this rust program to be executed as a script)
@[4](o/p: Hello world!)

---

Syntax and Tokens
=================

Before expanding further into the language concepts let us go through
its syntax and tokens, namely:

* keywords.
* Identifiers.
* Whitespace rules and meaning.
* Comments within rust program.
* Literals - char, strings, bool, number.
* Lifetimes and loop labels.
* Punctuations.
* Delimiters.
* Inventory of types.

---

Keywords
========

Keywords are identifier tokens that have special meaning. Keywords can
generally be classified between:

@ul
* **data** - @color[gray](false true box const let mut move ref self static)
* **control flow** - @color[gray](if else loop for while match break continue fn return)
* **type** - @color[gray](enum Self type struct trait unsafe where union impl)
* **compiler** - @color[gray](crate extern mod pub super self use)
@ulend

+++

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
* **Self** - inside **impl** and **trait** denotes the implementing type
@ulend

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

Similar to symbols in C, can be used to name items in a rust program. Like,

- **Tuple**, **struct**, **union**, **type-alias**. Start with uppercase and use camel-case. <br/> @color[blue](struct BigInt { ... })
- **Local variable-name**. Start with smallcase and use `_` as word separator. <br/> @color[blue](struct BigInt { int64 upper\_half, int64 lower\_half })
- **Constants** and **static name**. Use all UPPERCASE and use `_` as word separator. <br/> @color[blue](const LIMIT_START = 100\_i32)
- **Type parameter**. Use single uppercase alphabet. @color[blue](T, D)
- **Lifetime**. Use single lowercase alphabet, @color[blue]('_), @color[blue]('a), @color[blue]('b), @color[blue]('static).
- **Field-name** within struct and union. Same as local variable-name
- **Variant-name** within enumeration. Same as Type-name.
- **Function-name**. Same as local variable name.
- **Trait-name**. Same as type-name.
- **Associated types**. Same as Type-name
- **Module-name**. Same as local variable name.
- **Crate-name**. Same as local variable name.

+++

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

Literals
========

Literals are values that can be hardcoded in a rust program.

@ul
- **Character** literals.
- **String** literals.
- **Raw string** literals.
- **Byte** literals.
- **Byte string** literals.
- **Raw byte string** literals.
- **Integer** literals.
- **Float** literals.
- **Boolean** literals.
@ulend

---

Literals: Character and Strings
===============================

|				   | Example	| Characters	| Escapes
|---------------   |------------|---------------|-----------------------
| Character		   | 'H'		| All Unicode	| Quote & ASCII & Unicode
| String		   | "hello"	| All Unicode	| Quote & ASCII & Unicode
| Raw String       | r#"hello"#	| All Unicode	| N/A
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
- All number literals allow **_** as a visual separator: __1_234.0E+18f64__
- Integer suffixes - u8, i8, u16, i16, u32, i32, u64, i64, u128, i128, usize, isize
- Floating point suffixes - f32, f64
- By default integers are infered as **i32**.
- By default float is infered as **f32**.
@ulend

+++

Numbers: Example
================

@snap[number-example bg-white]
@color[blue](1000)
<br/> <br/>
As a mathematical value.
@snapend

@snap[number-example bg-white fragment]
@color[blue](1000u128)
<br/> <br/>
Number values can be typed with one of
u8, i8, u16, i16, u32, i32, u64, i64, u128, i128, usize, isize
@snapend

@snap[number-example bg-white fragment]
@color[blue](1000_u128)
<br/> <br/>
Use underscore to avoid clutter.
@snapend

@snap[number-example bg-white fragment]
@color[blue](1_000_000_u128)
<br/> <br/>
Use as many underscore to make it readable.
@snapend


---

Literals: Boolean
=================

Tokens **true** and **false** are treated as boolean literal to be used
as boolean-true and boolean-false respectively.

---

Lifetimes and loop-labels
=========================

---

Punctuations
============

The semicolon following a statement is not a part of the statement itself. They are invalid when using the stmt macro matcher.

---

Delimiters
==========

---

@title[Value]

@snap[midpoint text-center]
<h1 style="text-align: center !important;">Values</h1>
<br/>
All of programming is operating on @color[blue](values). In Rust, every
value has a single, specific @color[blue](type).
<br/> <br/>
When values of different types allow same @color[blue](operation),
then such an operation can be abstracted as a @color[blue](trait)
@snapend

+++

Memory layout
=============

All values for a given type have a pre-defined and identical memory-layout
that can be controlled via compiler-attributes.

In a rust program every value is either stored,
* as part of the machine instruction.
* or memory location, where memory can be stack or heap.

Variable names, either local or static, points to a memory location
in stack or heap.

There is a special type of value that points to a memory location. The
type of such values are called @color[blue](references) or @color[blue](pointers),
denoted with symbols @color[blue](&) and @color[blue](*). Examples,
* &int, &str, &String, &Vec
* \*int, \*str, \*String, \*Vec

And generically speaking - @color[blue](&T) and @color[blue](*T).

+++

Example
=======

<br/> <br/>

```rust
let x: i32 = 10 + 20;
let y: f64 = 10.2 + 20.5;
```

@[1](addition can be applied on integers - **i32**.)
@[2](addition can be applied on floating point - **f64**.)

<br/> <br/>

@snap[fragment]
In Rust, addition operation, denoted by its shortcut symbol @color[blue](+),
is abstracted as a trait - @color[blue](Add).
@snapend

---

@title[Types]

@snap[midpoint text-center]
<h1 style="text-align: center !important;">Types</h1>
<br/>
Every variable, item and value in Rust has a type. The type of a value
defines the interpretation of the memory holding it.
<br/>
In other words, a value can be treated as an instance of its type.
@snapend

---

Primitive types
===============

- **Boolean type**
- **Integer machine types - u8, u16, u32, u64, u128, i8, i16, i32, i64, i128**
- **Floating point - f32, f64**
- **Machine dependant integer types - isize, usize**
- **Textual types - char, str**
- **Never type !**
- **Unit type ()**

---

Complex types
=============

- **Array type**
- **Slice type**
- **Tuple type**
- **Structural type**
- **Union type**
- **Enumerated type**
- **Function item type**
- **Closure type**
- **Trait object type**
- **Function pointer**
- **Reference**
- **Pointer**

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
- **Unit type ()**, a tuple type with no element, equivalent of None.
  - Zero sized.
  - Alignment is 1.
  - All statements, when treated as expression, return a value of unit-type.
@ulend

---

Type: Array [T; N]
==================

An array is a fixed-size sequence of N elements of type T.

* **T** is a type identifier.
* **N** is size expression that evaluates to a @color[blue](usize).
* All elements of arrays are always initialized,
* Access to an array is always bounds-checked in safe methods and operators.

```rust
let array: [i32; 3] = [1, 2, 3];
let boxed_array: Box<[i32]> = Box::new([1, 2, 3]);
let array: Vec<i32> = vec![1,2,3,4];
```
@[1](A stack-allocated array.)
@[2](A heap-allocated array, coerced to a slice.)
@[3](A heap-allocated, re-sizable array.)

+++

Array: Construction
===================

```rust
[1, 2, 3, 4];
["a", "b", "c", "d"];
[0u8, 0u8, 0u8, 0u8,];
[[1, 0, 0], [0, 1, 0], [0, 0, 1]];
[0; 128];
```

An array expression can be written by enclosing zero or more
comma-separated expressions of uniform type in square brackets.

Alternatively, there can be exactly two expressions inside the brackets,
separated by a semi-colon - [a; b]
* **[a; b]** creates an array containing b copies of the value of a.
* If b evaluates to more than 1, type of a shall implement **Copy** trait.
* **b** must be a have type usize and be a constant expression.

Inner attributes are allowed directly after the opening bracket of an array.

+++

Array: Indexing
===============

Array indexing is implemented via Index and IndexMut traits, which
are implemented by default for [T; N] and [T] types.

* Index, std::ops::Index::index(&a, b)
* IndexMut, *std::ops::IndexMut::index_mut(&mut a, b)

where

* Indices are zero-based.
* **b** should be of type usize.
* Rust will also insert dereference operations on **a** repeatedly to find an implementation.

---

Type: Slice [T]
===============

* Dynamically sized type.

* **&[T]**, a 'shared slice', often just called a 'slice', it doesn't own the data it points to, it borrows it.
* **&mut [T]**, a 'mutable slice', mutably borrows the data it points to.
* **Box<[T]>**, a 'boxed slice'.
* All elements of slices are always initialized.
* Access to a slice is always bounds-checked in safe methods and operators.

---

Type aliases
============

```rust
type Point = (u8, u8);
let p: Point = (41, 68);

enum E { A }
type F = E;
let _: F = E::A;  // OK
// let _: F = F::A;  // Doesn't work
```

- A type alias defines a new name for an existing type.

@[1](defines the type Point as a synonym for the type \(u8, u8\).)
@[4-7](A type alias to an enum type cannot be used to qualify the constructors.)

---

Type: Tuple
===========

* Heterogeneous product of other types.
* Has no nominal name.
* Structurally typed.

Tuple elements can be accessed by:

* Pattern-matching.
* Using N directly as a field to access the Nth element.
* Inner attributes are allowed directly after the opening parenthesis
of a tuple expression. All attributes applicable on block expression
are applicable on tuple.

```rust
type Pair<'a> = (i32, &'a str);
let p: Pair<'static> = (10, "ten");
let (a, b) = p;

assert_eq!(a, 10);
assert_eq!(b, "ten");
assert_eq!(p.0, 10);
assert_eq!(p.1, "ten");
```

+++

Tuple constructor
=================

```rust
(0.0, 4.5);
("a", 4usize, true);
();
let unit_x = Point(1.0, 0.0);
```

Single element tuple:

```rust
(0,);
(0);
```

@[5](single-element tuple.)
@[6](zero in parentheses.)

+++

Tuple access
============

Tuples can be indexed using the number corresponding to the
position of the field. The index must be written as a
decimal literal with no underscores or suffix.

---

Structural type
===============

```rust
struct Point {x: i32, y: i32}
let p = Point {x: 10, y: 11};
let px: i32 = p.x;

struct Point(i32, i32);
let p = Point(10, 11);
let px: i32 = match p { Point(x, _) => x };

struct Cookie;
let c = [Cookie, Cookie {}, Cookie, Cookie {}];
```

@ul[mt20]
- A struct type is a heterogenous product of other types, called the **fields** of the type.
- Structural types can be defined in two forms **Tuple** and **struct**.
- A **unit-like** struct is a struct without any fields, defined by leaving off the list of fields entirely.
- Memory layout of a struct is undefined by default to allow for optimizations, nevertheless it can be fixed using the **#[repr(...)]** attribute.
@ulend

@[1](struct declaration.)
@[2](struct construction.)
@[3](struct expression.)
@[5](tuple declaration.)
@[6](tuple construction.)
@[7](tuple expression.)
@[9-10](unit-like struct.)

+++

Struct examples
===============

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

Enum
====

An Enumerated type, in its simplest form, is possible set of values
that the enumerated-type can have.

```rust
enum PrimaryColors {
	Red,
	Green,
	Blue,
}
```

Here **PrimaryColors**, although internally it is represented as an integer,
can only have one of the three values **Red**, **Green**, **Blue**.

+++

Enum types
==========

```rust
enum IpAddrKind {
    V4(String),
    V6(String),
}
```

@snap[mt20 fragment]
Rust's version of enumerated type not only implement the simplest
form of enumerating values, but also provide a powerful way to
combine related types as a variant of a more generic type.
@snapend

@snap[mt20 fragment]
Here we see that IP-Address can be 4-byte variant, <b>v4</b>, defined by
the old version-4 spec, or, 16-byte variant, <b>v6</b>, defined by the
latest version-6 spec.
@snapend

@snap[mt20 fragment]
Similar to struct, each enumerated variant follow the syntax of:
@snapend

@ul
* Unit-like variant, with no fields.
* Tuple like variant, with positional fields.
* Struct like variant, with named fields.
@ulend

@snap[mt20 fragment]
Any enum value consumes as much memory as the largest variant for its corresponding enum type, as well as the size needed to store a discriminant.
@snapend

+++

Enum: custom discriminant
=========================

```rust
enum Foo {
    Bar,            // 0
    Baz = 123,      // 123
    Quux,           // 124
}

let baz_discriminant = Foo::Baz as u32;
assert_eq!(baz_discriminant, 123);

#[repr(u8)]
enum SmallSizedDiscriminant {
    Zero,
    One,
}

enum ZeroVariants {}
```

@[1-5](Each enum instance has a discriminant which is an integer associated to it that is used to determine which variant it holds.)
@[7-8](These enumerations can be cast to integer types with the as operator by a numeric cast.)
@[1-5](Under the default-representation, the specified discriminant is interepreted as an **isize**.)
@[10-14](Discriminant size can be changed using the **repr** attribute.)

+++

Enum: construction
==================

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

---

Union
=====

In many aspects unions behave exactly like structs. Except,

* Layout
  * The key property of unions is that all fields of a union share
    common storage.
  * Size of a union is determined by the size of its largest field.
* Safety
  * Active field in a union is not generally known statically,
    so all reads and pattern matching of union fields have to be
    placed in ``unsafe`` blocks.
* Ownership
  * If one field of a union is borrowed all its remaining fields are borrowed as well.

+++

Union example
=============

```rust
#[repr(C)]
union MyUnion {
    f1: u32,
    f2: f32,
}

fn f(u: MyUnion) {
    let u = MyUnion { f1: 1 };
	unsafe {
		let f = u.f1;
	}
    unsafe {
        match u {
            MyUnion { f1: 10 } => { println!("ten"); }
            MyUnion { f2 } => { println!("{}", f2); }
        }
    }
	u.f1 = 2;
}

```

@[2-5](Defining a union type.)
@[8](The expression creates a value of type MyUnion with active field f1.)
@[9-11](Reads are unsafe.)
@[12-17](Pattern matching is allowed, as a read operation, which again is unsafe.)
@[18](Writes to Copy union fields do not require reads for running destructors, so these writes don't have to be placed in unsafe blocks.)

---

Functions
=========

```rust
fn answer_to_life_the_universe_and_everything() -> i32 {
    return 42;
}
fn first((value, _): (i32, i32)) -> i32 {
    value
}
```

@ul[mt20]
- Function's arguments are **irrefutable patterns**, similar to **let** bindings.
- A function is conceptually wrapped in a block that binds the argument patterns and then returns the value of the function's block.
- Tail expression of the a block, if evaluated, implicitly becomes the return value from the block.
- An explicit return expression can be used, anywhere in the block, to short-circuit the implied tail-return.
@ulend

+++

Generic functions
=================

```rust
fn foo<A, B>(x: A, y: B) {
}

// Trait bounds, using where syntax
fn bar<T>(x: T) where T: Debug -> bool {
	if mem::size_of::<T>() == 4 { return true }
	return false
}
```

@ul[mt20]
- Function `foo` is parametrised over types `A` and `B`.
- Inside the function signature and body, the name of the type parameter can be used as type-name.
- Trait bounds can be specified for the type-parameters to allow methods from that trait to be called on the values.
@[6](It is necessary, if there is not sufficient context to determine the type parameters, to supply the type parameters explicitly in a trailing path component after the function name.)
@ulend

+++

Extern functions
======================

```rust
extern fn new_i32() -> i32 { 0 }
extern "stdcall" fn new_i32_stdcall() -> i32 { 0 }
```

@ul[mt20]
- Provide the opposite functionality to external blocks which allow Rust code to call foreign code.
- Also called as extern functions, can be called by foreign code.
@ulend

@[1](Declares an extern fn, the ABI defaults to "C".)
@[2](Declares an extern fn with "stdcall" ABI.)

+++

Function attributes
===================

```rust
#[test] // Outer attributes are allowed on functions.
fn test_function() {
}
fn test_another_function() {
	!#[test] // Inner attributes are allowed immediately after the function signature.
}
```

Attributes that are allowed on functions:

@ul
* cfg
* deprecated
* doc
* export_name
* link_section
* no_mangle
* allow, deny, forbid, warn
* must_use
* procedural macros
* test
* cold, inline
@ulend

---

@title[Traits]

@snap[midpoint text-center]
<h1 style="text-align: center !important;">Traits</h1>
<br/>
A Trait can be called as @color[blue](behaviour of values).
<br/>
Typically when a behaviour is common between two or more types, it becomes
a good candidate to be abstracted as a trait.
<br/> <br/>
In other words, a Trait can be used to enrich one or more types.
@snapend

---

Trait: Items
============

A trait can have following associated items:

* Functions
* Types
* Constants

Traits are implemented for specific types through separate
implementations. Typically Traits are
defined first, and types implement them by bring them into scope,
either in the same crate or in a different crate.

* A trait definition can refer to the implementing type, without knowing
  the type-name, using the Self keyword.
* Items associated with a trait can have a default definition. In which
  case, types can choose to skip or override the item definition.
* Traits can be added as bounds (aka where clause contraints) on
  type-parameters.
* Traits, can also be parametrised over types and lifetimes.

---

Trait: Object and safety
========================

A trait object is an opaque value of another type that implements
a set of traits. The set of traits is made up of an object safe
base trait plus any number of auto traits.

For a trait to be object-safe:

* It must not have any associated constants.
* It must not require Self: Sized
* All associated functions must either have a where Self: Sized bound, or
  * Not have any type parameters (although lifetime parameters are allowed), and
  * Be a method that does not use Self except in the type of the receiver.
* All supertraits must also be object safe.

---

Trait: Super traits
===================

Super traits can be used to create a dependency chain of traits. That is,
to implement a specific trait, types must also implement the trait's super
traits. It also means that all associated items of super-traits are
implicitly available as part of the trait.

It is an error for a trait to be its own supertrait.

```rust
trait Shape { fn area(&self) -> f64; }
trait Square : Shape { fn side(&self) -> f64; }
trait Circle where Self: Shape {
    fn radius(&self) -> f64 {
        // A = pi * r^2, so algebraically, r = sqrt(A / pi)
        (self.area() /std::f64::consts::PI).sqrt()
    }
}

let circle = Box::new(circle) as Box<dyn Circle>;
```

@[1](Shape is the super trait.)
@[2](Square is the sub trait of Shape, and area-method is available on types implementing Square.)
@[3](Circle is sub-trait of Shape defined used where clause, an alternate syntax.)
@[4-7](Default definition for radius, implementing type can choose to skip radius, or override it.)
@[9](Making a trait-object.)

---

@title[Implementation]

@snap[midpoint text-center]
<h1 style="text-align: center !important;">Implementations</h1>

<br/>

Types can be enriched by associating other items, like **constants**,
**functions**, **types**, using an @color[blue](implementation) block.

<br/> <br/>

Types can also be enriched by implementing traits.
@snapend

---

Inherent implementation
=======================

```rust
struct Point {x: i32, y: i32}

impl Point {
    fn log(&self) {
        println!("Point is at ({}, {})", self.x, self.y);
    }
}

let my_point = Point {x: 10, y:11};
my_point.log();
```

@ul[mt20]
* Associate items to the implementing type.
* Path of the associated item is the path to the implementing type followed by item's path component.
* No type aliases.
* An implementing type must be defined within the same crate as the original type definition
@ulend

---

Trait implementation
====================

* A trait implementation must define all non-default associated items
  declared by the trait.
* Can override default associated items defined by the trait.
* Cannot define any other items.
* Path of associated item is TODO **<path::to::type as associated::item>**.

Type parameters declared for an implementation must be used at least
once in either the trait or the implementing type of an implementation.

```rust
struct Circle {
    radius: f64,
    center: Point,
}

impl Copy for Circle {}

impl Clone for Circle {
    fn clone(&self) -> Circle { *self }
}

impl Shape for Circle {
    fn draw(&self, s: Surface) { do_draw_circle(s, *self); }
    fn bounding_box(&self) -> BoundingBox {
        let r = self.radius;
        BoundingBox{x: self.center.x - r, y: self.center.y - r, width: 2.0 * r, height: 2.0 * r}
    }
}
```

+++

Trait coherence
===============

A trait implementation is considered incoherent, if:

* either, the orphan check fails.
* or, there are overlapping implementation instances.

TODO: What is overlapping trait-implementation.

Orphan check must satisfy either of the following conditions:

* The trait being implemented is defined in the same crate.
* At least one of either Self or a generic type parameter of the
  trait must meet the following grammar, where C is a nominal
  type defined within the containing crate:

```bnf
 T = C
   | &C
   | &mut C
   | Box<C>
```

---

Associated items
================

Associated Items are the items declared/defined in @color[blue](traits)
or defined in @color[blue](implementations). Defined on a type.
Logically related to the type. Enrich the behaviour of the type.

Associated items can be:
* Associated functions.
* Associated methods.
* Associated constants.
* Associated types.

They come in two varities:

* @color[blue](Definitions) that contain the actual implementation.
* @color[blue](Declarations) that declare signatures for definitions.

Unless otherwise specified, both variants can be present in a trait
or implementation.

+++

Associated functions
====================

```rust
struct Struct {
    field: i32
}
impl Struct {
    fn new() -> Struct {
        Struct {
            field: 0i32
        }
    }
}

trait Num {
    fn from_i32(n: i32) -> Self;
}
impl Num for f64 {
    fn from_i32(n: i32) -> f64 { n as f64 }
}

fn main () {
    let _struct = Struct::new();
	let _f: f64 = <f64 as Num>::from_i32(42);
}
```

* Declaration of associated function is written as a function item,
  except the function body is replaced with a @color[blue](**;**).
* Definition of associated function is written the same as a function item.

@[5-9](Associated function definition implemented on a type.)
@[16](Associated function definition implemented on a trait.)
@[21](Associated function on a triat can be invoked using trait-path.)

+++

Associated method
=================

```rust
trait Shape {
    fn draw(&self, Surface);
    fn bounding_box(&self) -> BoundingBox;
}
struct Circle {
    // ...
}
impl Shape for Circle {
    // ...
}

let circle_shape = Circle::new();
let bounding_box = circle_shape.bounding_box();
```

Associated functions whose first parameter is named **self** are called
methods.

@[1-4](All values that have implementations of this trait while the trait is in scope can have their draw and bounding_box methods called.)
@[13](Methods are invoked using method call operator.)

+++

Associated method: self
=======================

The **self** parameter come in following variants and an equivalent shortcut:

type                | shortcut
--------------------|-----------
self                | self: Self
&'lifetime self     | self: &'lifetime Self
&'lifetime mut self | self: &'lifetime mut Self
self : Box &#60;Self&#62;    | (no shorthand)

Lifetimes can be and usually are elided with this shorthand.

+++

Associated types
================

* Associated types cannot be defined in inherent implementations.
* Nor can they be given a default implementation in traits (unstable).
* Declaration of associated type @color[blue]({type-keyword, identifier, optional list of trait bounds}).
* Definition of associated type @color[blue]({type-keyword, identifier, =, type-name}.)

```rust
trait AssociatedType {
    type AssocDecl : Copy;
}

struct Struct;
#[derive(Copy)]
struct OtherStruct;

impl AssociatedType for Struct {
    type Assoc = OtherStruct;
}
impl OtherStruct {
    fn new() -> OtherStruct {
        OtherStruct
    }
}
fn main() {
    let _other_struct: OtherStruct = <Struct as AssociatedType>::Assoc::new();
}
```

@[2](Associated type declaration.)
@[6](The optional trait bounds must be fulfilled by the implementations of the type alias.)
@[10](Associated type definition.)
@[18](Refering to associated type.)

+++

Associated items trait impl
===========================

```rust
trait Container {
    type E;
    fn empty() -> Self;
    fn insert(&mut self, Self::E);
}
```

In order for a type to implement this trait, it must not only
provide implementations for every method, but it must specify
the type E.

Here's an implementation of Container for the standard library type Vec:

```rust
impl<T> Container for Vec<T> {
    type E = T;
    fn empty() -> Vec<T> { Vec::new() }
    fn insert(&mut self, x: T) { self.push(x); }
}
```

@[4](Associated types can be refered within a trait block as a type parameter.)

+++

Associated constants
====================

```rust
trait ConstantId {
    const ID: i32;
    const ID_F: f64 = 1.0;
}

struct Struct;

impl ConstantId for Struct {
    const ID: i32 = 1;
}

fn main() {
    assert_eq!(1, Struct::ID);
}
```

* Declaration of associated constant declares a signature for
  associated constant definitions. It is written as
  {const, identifier, :, type-name, ;}
* Definition of associated constant defines a constant associated
  with a type. It is written the same as a constant item.

@[1](Associated constant declaration.)
@[2](Associated constant declaration, with default value.)
@[9](Associated constant definition.)

+++

Items in a block
================

```rust
fn scoping_fn() {
    const X: u32 = 10;
    static Y: u32 = 20;
    extern crate std;
    use std::i16::MAX;

    mod level1 {
        pub const Z: u32 = 30;
    }

    #[derive(Debug)] struct T { a: u32 };
    trait TT { fn as_float(&self) -> f64; }
    impl T {
        fn new(a: u32) -> T { T{a} }
    }
    impl TT for T {
        fn as_float(&self) -> f64 { f64::from(self.a) }
    }

    fn local_fn() -> bool { true }
    let t = T::new(200);
    println!("{} {} {}", X, Y, MAX);
    println!("{} {:?} {:e} {}", level1::Z, t, t.as_float(), local_fn());
}
```

All the above items are allowed either in a function or a block, and
they are restricted to the function or block in which they are defined.

@[2](Constant declaration.)
@[3](Static declaration.)
@[4](External crate declaration.)
@[5](Use declaration.)
@[7-9](Module declaration.)
@[11](Struct type declaration, similarly type alias, union and enumeration are allowed.)
@[12](Trait definition.)
@[13-15](Inherent implementation.)
@[16-18](Trait implementation.)
@[20](Function item.)

---

Statements
==========

A statement is a component of a block, which in turn is a component of
outer expression or function.

Two kinds of statements:

* Declaration statements
* Expression statements

---

Declaration statements
======================

Two kinds of declaration statements

* Item declaration, that includes all types of item declaration.
  * Items are not given any canonical path, which means restricted
    local scope.
  * Except, associated items.
* Let declaration, introduce a new set of variables into local scope.

```rust
fn outer() {
  let outer_var = true;

  fn inner() { /* outer_var is not in scope here */ }

  inner();
}
```

@[4](There is no implicit capture of the containing function's generic parameters, parameters, and local variables.)

---

Expression statements
=====================

An expression statement is one that evaluates an expression and
ignores its result. All expression statement are supposed to end with a
semi-colon and the end result is unit-type ().

---

Expressions
===========

Rust is primarily an expression language.
Most forms of value-producing or effect-causing evaluation
are directed by the unifor syntax category of expressions.

Expression evaluation is determined by precedence and
associativity rules.

---

Kinds of expressions
====================

Literal expressions.
PathExpression

BlockExpression

OperatorExpression
GroupedExpression
ArrayExpression
IndexExpression
TupleExpression
TupleIndexingExpression
StructExpression
EnumerationVariantExpression
CallExpression
MethodCallExpression
FieldExpression

ClosureExpression

LoopExpression
ContinueExpression
BreakExpression
RangeExpression
IfExpression
IfLetExpression
MatchExpression
ReturnExpression

---

Path Expression:

A path used as an expression context denotes either a local variable
or an item.

Path expressions that resolve to local or static variables are place
expressions.

Others paths are value expression

---

Block expression
================

```rust
{
   "optional inner attributes"
   "zero or more statements";
   "optional expression"
}
```

* Blocks are always value expressions.
* Evaluate the last expression in value expression context.
* This can be used to force moving a value if really needed.

Different forms of block expression:

* Function and method bodies.
* Loop bodies (loop, while, while let, and for)
* Control flow (if and if let).

+++

Block type
==========

Like all expressions, block expressions are typed. The type of a
block is the type of the final expression, or () if the final
expression is omitted.

```rust
let _: () = {
    fn_call();
};

let five: i32 = {
    fn_call();
    5
};

assert_eq!(5, five);
```

+++

Evaluating blocks
=================

**Scope**

* Item declarations are only in scope inside the block itself
* Let declarations variables declared by let statements are in scope from
the next statement until the end of the block.

When evaluating a block expression, each statement, except for item
declaration statements, is executed sequentially.

Then the final expression is executed, if given, and its value is treated
as block expression's value, else it is **()**.

+++

Unafe blocks
============

A block of code can be prefixed with the unsafe keyword to permit
unsafe operations. Examples:

```rust
unsafe {
    let b = [13u8, 17u8];
    let a = &b[0] as *const u8;
    assert_eq!(*a, 13);
    assert_eq!(*a.offset(1), 17);
}

let a = unsafe { an_unsafe_fn() };
```

* Bound check on array is disabled.

+++


Block attributes
================

Inner attributes are allowed directly after the opening brace
of a block expression in the following situations

The attributes that have meaning on a block expression are
cfg and the lint check attributes.

Example:

```rust
fn is_unix_platform() -> bool {
    #[cfg(unix)] { true }
    #[cfg(not(unix))] { false }
}
```

---

Type Parametrisation
=====================

In Rust, @color[blue](types) and @color[blue](logic) can be parametrised
over other types. More specifically,

* Type aliases
* Struct
* Union
* Enumeration
* Functions
* Traits
* Implementations

References, raw pointers, arrays, slices, tuples and function pointers
have lifetime or type parameters as well, but are not referred to with
path syntax.

+++

Type params: Attributes
=======================

Generic lifetime and type parameters allow attributes on them.

```rust
// Assume that the derive for MyFlexibleClone declared `my_flexible_clone` as
// an attribute it understands.
#[derive(MyFlexibleClone)] struct Foo<#[my_flexible_clone(unbounded)] H> {
    a: *const H
}
```

---

Trait and lifetime bounds
=========================

Type parameters can be constrained using trait bounds and lifetime bounds,
using the **where clause**.

Bounds that don't use the item's parameters or higher-ranked lifetimes
are checked when the item is defined. It is an error for such a bound to
be false.

It is an error to have **Copy** or **Clone** as a bound on,

* A mutable reference
* trait object
* slice

It is an error to have **Sized** as a bound on,

* a trait object
* slice.




---

Higher ranked trait bounds
==========================

Type bounds may be higher ranked over lifetimes. These bounds specify
a bound is true for all lifetimes.

```rust
fn call_on_ref_zero<F>(f: F) where F: Fn(&'a i32) {
    let zero = 0;
    f(&zero);
}
```

Will throw following compiler error:

```text
error[E0261]: use of undeclared lifetime name `'a`
 --> hklt.rs:1:44
  |
1 | fn call_on_ref_zero_<F>(f: F) where F: Fn(&'a i32) {
  |                                            ^^ undeclared lifetime
```

To mitigate this error, we must associate ``'a`` lifetime to one
of the input parameters.

+++

Parametrise over lifetime
=========================

```rust
fn call_on_ref_zero<'a, F>(f: F) where F: Fn(&'a i32) {
    let zero = 0;
    f(&zero);
}
```

Will throw following compiler error:

```text
error[E0597]: `zero` does not live long enough
 --> hklt.rs:3:8
  |
3 |     f(&zero);
  |        ^^^^ borrowed value does not live long enough
4 | }
  | - borrowed value only lives until here
  |
  note: borrowed value must be valid for the lifetime 'a as defined on the function body at 1:23...
 --> hklt.rs:1:23
  |
1 | fn call_on_ref_zero__<'a, F>(f: F) where F: Fn(&'a i32) {
  |                       ^^
```

Only a higher-ranked bound can be used here as the lifetime of the
reference is shorter than a lifetime parameter on the function

+++

Higher ranked lifetimes
=======================

By using the special ``for`` syntax on the where clause we can define
higher ranked lifetimes for the trait bounds.

```rust
fn call_on_ref_zero<F>(f: F) where for<'a> F: Fn(&'a i32) {
    let zero = 0;
    f(&zero);
}
```

Alternative we can specify the higher-ranked lifetime just before the trait,
the difference being that the lifetime's scope is restricted to the trait.

```rust
fn call_on_ref_zero<F>(f: F) where F: for<'a> Fn(&'a i32) {
    let zero = 0;
    f(&zero);
}
```

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

@title[Items]

@snap[midpoint text-center]
<h1 style="text-align: center !important;">Items</h1>
<br/>
Rust program is organised as artifacts called items, and attributes that control the properties of specific item.
@snapend

---

Inventory of Items
==================

<table class="items-left">
<tr><td class="text-gray"> constant items </tr></td>
<tr><td class="text-gray"> static items </tr></td>
<tr><td class="text-blue"> module </tr></td>
<tr><td class="text-blue"> extern crate declaration  </tr></td>
<tr><td class="text-blue"> use declarations </tr></td>
<tr><td class="text-blue"> extern blocks </tr></td>
</table>

<table class="items-right">
<tr><td class="text-brown"> type definitions </tr></td>
<tr><td class="text-brown"> struct definitions </tr></td>
<tr><td class="text-brown"> enumeration definitions </tr></td>
<tr><td class="text-brown"> union definitions </tr></td>
<tr><td class="text-green"> function definitions </tr></td>
<tr><td class="text-green"> trait definitions  </tr></td>
<tr><td class="text-green"> implementations  </tr></td>
</table>

<br/> <br/> <br/> <br/> <br/> <br/> <br/> <br/> <br/> <br/>

@ul
* @color[blue](Module) is used to create a namespace for related set of items. They are also used to organise rust program into files and directories.
* @color[blue](Functions) can contain any other item, but they are scoped within the function. Items defined inside the function is not publicly visible to other items.
* @color[blue](Trait) and @color[blue](Implementations) can associate type, constants and functions to enrich a type.
@snapend


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

Constant Items
==============

* Named constant value, not associated with a specific memory location in the program.
* When the name goes out of scope, its destructors are run.
* Inlined wherever they are used.
* Constants must be explicitly typed
* The type, and references, must have a __'static__ lifetime.
* Constants may refer to the address of other constants

+++

Constant: Examples
==================

```rust
const BIT1: u32 = 1 << 0;
const BIT2: u32 = 1 << 1;

const BITS: [u32; 2] = [BIT1, BIT2];
const STRING: &'static str = "bitstring";

struct BitsNStrings<'a> {
    mybits: [u32; 2],
    mystring: &'a str,
}

const BITS_N_STRINGS: BitsNStrings<'static> = BitsNStrings {
    mybits: BITS,
    mystring: STRING,
};
```

@[1](named constant values.)
@[2](constants must be explicitly typed.)
@[4](inlined wherever they are used.)
@[5](the type, and references, must have a __'static__ lifetime.)
@[7-15](constants may refer to the address of other constants.)

+++

Constants with Destructors
==========================

In Rust destructors are implemented using the **Drop** trait. Constants
can contain destructors. Destructors are run when the value goes out of
scope.

```rust
struct TypeWithDestructor(i32);
impl Drop for TypeWithDestructor {
    fn drop(&mut self) {
        println!("Dropped. Held {}.", self.0);
    }
}

const ZERO_WITH_DESTRUCTOR: TypeWithDestructor = TypeWithDestructor(0);

fn create_and_drop_zero_with_destructor() {
    let x = ZERO_WITH_DESTRUCTOR;
}
```

@[1-6](TypeWithDestructor implementing a destructor.)
@[8](declaring a constant for TypeWithDestructor.)
@[13](**x** gets dropped at end of function, calling drop. prints "Dropped. Held 0.".)

---

Static items
============

Static items are similar to constant items, except for:

* It represents a precise memory location.
* Have static lifetime.
* Do not call Drop at the end of the program.

If a static item is non-mutable, that is not interior mutable can be placed
is read-only memory.

All access to static items are safe, except:
* Item's type must have a Sync trait to allow thread-safe access.
* Static may refer other statics only through a reference, except when using
paths to statics in constant expression.
* Constants cannot refer to statics.

+++

Mutable statics
===============

If a static item is declared with the mut keyword, an unsafe block is
required to read or write the static item.

Mutable statics have the same restrictions as normal statics, except
that the type does not have to implement the Sync trait.

---

Statics or Constants
====================

Constants should, in general, be preferred over statics unless one of the following are true:

* Large amounts of data are being stored
* The single-address property of statics is required.
* Interior mutability is required.

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

Static lifetime
===============

* Outlives all other lifetimes.

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

External blocks
===============

---

List of presentations
=====================

* Attributes
* Traits
* Move semantics
* Pattern matching
* Refutable bindings and Irrefutable bindings
* Parametric Types
* Lifetimes - static, stack, heap
* Safety
* Mono-morphisation
* Macro

https://blog.rust-lang.org/2018/11/27/Rust-survey-2018.html

---

Attributes
==========

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

Attributes that have meaning for an ``implementation``
cfg, deprecated, doc, and the lint check attributes.

Type params: Attributes

	Generic lifetime and type parameters allow attributes on them.

	```rust
	// Assume that the derive for MyFlexibleClone declared `my_flexible_clone` as
	// an attribute it understands.
	#[derive(MyFlexibleClone)] struct Foo<#[my_flexible_clone(unbounded)] H> {
		a: *const H
	}
	```

Attributes on statements:

    Statements accept outer attributes.
    The attributes that have meaning on a statement are cfg, and the lint
    check attributes.


---

Presentation on traits
======================

Auto-traits :
Core-traits :

Termination

---

Questions
=========

What are the limitations of user defined types ?
Are there any special significance attached to main.rs ?
Are there any special significance attached to lib.rs ?
what is "const fn" ?

