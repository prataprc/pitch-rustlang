@title[Rust Documentation tool]

@snap[midpoint text-center span-60]
<h1 style="text-align: center !important">Documentation for Rust Crate</h1>
code · document · publish
@snapend


@snap[south-east author-box]
@fa[envelope](prataprc@gmail.com - R Pratap Chakravarthy) <br/>
@snapend

---

Rustdoc work-flow
=================

@img[rustdoc-workflow](./rustdoc/rustdoc_work_flow.svg)

+++

Example 1: crate documentation
==============================

<br>

Generating documentation for a crate.

```rust
/// foo is a function
pub fn foo() {}
```

Above crate contain a function ``foo``, with documentation.

```bash
$ rustdoc src/lib.rs --crate-name docs
```
+++

Example 2: standalone markdown file
===================================

``rustdoc`` can also generate HTML from standalone Markdown files.

```md
# Docs

This is a project to test out `rustdoc`.

[Here is a link!](https://www.rust-lang.org)

## Subheading

 ```rust
 fn foo() -> i32 {
     1 + 1
 }
 ```
```

And call rustdoc on it:

```rust
$ rustdoc README.md
```

Generates ``docs/doc/README.html``.

---?id=test

Compiler support
================

<br>

Rust programs are organised as collection of items that can be
compiled to binary form. When it comes to documenting rust code,
following compiler features matter:

<br>

@ul
* Public items that are visibile to users.
* Items can be attributed using ``#[doc]``.
* Doc comments and non-doc comments.
@ulend

---

Comments and documentation
==========================

Rich documentation from code and comments.

@snap[fragment]
``Non-doc-comments``, like C++:
@snapend

@ul[mt30]
* line-comments.
* block-comments.
@ulend

@snap[fragment mt30]
``Doc-comments``, interpreted in markdown-syntax compiled to
HTML/CSS/Javascript, come in four flavours:
@snapend

@ul[mt30]
* Inner-line-comments.
* Inner-block comments.
* Outer-line-comments.
* Outer-block-comments.
@ulend

+++

Example 1: Line comment
=======================

```rust
//! A doc comment that applies to the implicit anonymous module of this crate
pub mod outer_module {
    //!  - Inner line doc
    //!! - Still an inner line doc (but with a bang at the beginning)

    //   - Only a comment
    ///  - Outer line doc (exactly 3 slashes)
    //// - Only a comment

    pub mod degenerate_cases {
        // empty inner line doc
        //!

        // empty line comment
        //

        // empty outer line doc
        ///

    }
    /// Where is my item?
}
```

+++

Example 2: Block comments
=========================

```rust
pub mod outer_module {
    /*!  - Inner block doc */
    /*!! - Still an inner block doc (but with a bang at the beginning) */

    /*   - Only a comment */
    /**  - Outer block doc (exactly) 2 asterisks */
    /*** - Only a comment */

    /* In Rust /* we can /* nest comments */ */ */

    pub mod degenerate_cases {
        // empty inner block doc
        /*!*/

        // empty block comment
        /**/

        // empty 2-asterisk block isn't a doc block, it is a block comment
        /***/
    }
    /* The next one isn't allowed because outer doc comments
       require an item that will receive the doc */
}
```

---

Doc attribute
=============

Every documentation that matters to @color[blue](``rustdoc``) is
via doc-attribute.

Say,

```rust
/// This is a doc comment.
fn myfunc() {
    // TBD
}
```

Is equivalent to:

```rust
#[doc = " This is a doc comment."]
fn myfunc() {
    // TBD
}
```

+++

And for outer doc-comment ...
=============================

<br>

```rust
//! This is a doc comment.

fn myfunc() {
    // TBD
}
```

Is equivalent to:

```rust
#![doc = " This is a doc comment."]

fn myfunc() {
    // TBD
}
```

---

Useful doc attributes
=====================

* Favicon
* Logo

+++

Doc-attr: Favicon
=================

<br>

```rust
#![doc(html_favicon_url = "https://cdn4.iconfinder.com/json.png")]
#![doc(html_logo_url="https://upload.wikimedia.org/JSON_vector_logo.svg")]
```

Will insert,

```html
<link rel="shortcut icon" href="https://cdn4.iconfinder.com/data/icons/fugue/icon_shadowless/json.png">
<a href="../jsondata/index.html"><div class="logo-container">< img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/JSON_vector_logo.svg/1024px-JSON_vector_logo.svg.png" alt="logo"></div>  </a>
```

into final docs.

@img[rustdoc-favicon-logo](./rustdoc/jsondata_fav_logo.png)

---

Doc comments are transformed into doc attributes.
