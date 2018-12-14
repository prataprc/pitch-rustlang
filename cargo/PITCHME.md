@title[Cargo]

@snap[midpoint slide1 span-80]
<h1>Cargo</h1>
built . test . package . distribute . install
@snapend


@snap[south-east author-box]
@fa[envelope](prataprc@gmail.com - R Pratap Chakravarthy) <br/>
@snapend

---

Rust program
============

The compilation unit of rust program is called a @color[blue](crate),
where crates can be further organised as @color[blue](modules),
in separate @color[blue](files) and @color[blue](directories).

A module in rust program is an @color[blue](item) that wraps
up all other items, scoping them within a namespace.
The compilation unit starts with anonymous module, whose name is same
as the name of the crate.

Each crate produces an output that is either:

* A Binary, crate that contains a main() function.
* A Library

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

Every source file is a module, but not every module needs a source file.

---

File and directories
====================

There is a nifty way to map module name into file-name and directory name
and there by organising code in multiple files and directories:

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
