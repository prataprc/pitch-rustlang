@title[Cargo]

@snap[midpoint slide1 span-80]
<h1>Cargo</h1>
build . test . package . distribute . install
@snapend


@snap[south-east author-box]
@fa[envelope](prataprc@gmail.com - R Pratap Chakravarthy) <br/>
@snapend

---

Rust program
============

The compilation unit of rust program is called a @color[blue](crate),
where crates can be further organized as @color[blue](modules),
in separate @color[blue](files) and @color[blue](directories).

A module in rust program is an @color[blue](item) that wraps
up all other items, scoping them within a name-space.
The compilation unit starts with anonymous module, whose name is same
as the name of the crate.

Each crate produces an output that is either:

* A Binary crate that contains a main() function.
* A Library crate built from @color[blue](lib.rs)

Cargo is the build system shipped along with rust tool-chain.

---

Modules
=======

Example:

```bash
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
and there by organizing code in multiple files and directories:

```bash
mod vec; // Load the `vec` module from `vec.rs`
mod util; // Load from util/mod.rs
mod thread {
    // Load the `local_data` module from `thread/local_data.rs`
    // or `thread/local_data/mod.rs`.
    mod local_data;
}
```

@snap[module-tree]
![TREE](./cargo/module-tree.png) // TODO: move this to asset/ sub-directory
@snapend

<br/>

* A module without a body is loaded from an external file.
* If module name is matching with a directory, then load from a default
module called @color[blue](mod.rs).
* When a directory does not have a mod.rs, then the parent module can
include files under sub-directories by nested module declaration.


---

Command matrix
==============

Following is a common set of commands used during each phase of
working with a rust project:

develop       | build             | test  | package        | distribute  | install
--------------|-------------------|-------|----------------|-------------|---------
 new          | check             | test  | metadata       | login       | install
 init         | build             | bench | locate-project | owner       | search
 fix          | doc               |       | package        | publish     | uninstall
 git-checkout | generate-lockfile |       | pkgid          | yank        | update
 run          | fetch             |       | read-manifest  |             |
              | clean             |       |                |             |

+++

Commands: Development
=====================

* **new**, create a new package.
* **init**, create a new package in an existing directory.
* **fix**, automatically fix link warnings reported by ``rustc``.
* **git-checkout**, checkout a copy of a git repository.
* **run**, run the main binary of the local package, ``src/main.rs``.

+++

Commands: Build
===============

* **check**, check a local package and all of its dependencies for errors.
* **build**, compile a local package and all of its dependencies.
* **doc**, build a package's documentation.
* **generate-lockfile**, generate the lockfile for a project.
* **fetch**, fetch dependencies of a package from the network.
* **clean**, remove artifacts that cargo has generated in the past.

+++

Commands: Test
==============

* **test**, execute all unit and integration tests of a local package.
* **bench**, execute all benchmarks of a local package.

+++

Commands: Packaging
===================

* **metadata**, output the resolved dependencies of a project.
* **locate-project**, output the resolved dependencies of a project.
* **package**, assemble the local package into a distribution.
* **pkgid**, print a fully qualified package specification.
* **read-manifest**, print a JSON representation of a Cargo.toml manifest.

+++

Commands: Distribute
====================

By default cargo uses crates.io registry.

* **login**, save an API token from the registry locally.
* **owner**, manage the owners of a crate on the registry.
* **publish**, upload a package to the registry.
* **yank**, remove a pushed crate from the index

A published version of a crate cannot be deleted.

+++

Commands: Install
=================

* **install**, install a rust binary.
* **search**, search packages in crates.io
* **uninstall**, remove a rust binary.
* **update**, update dependencies as recorded in the local lock file.

---

Package layout
==============

@img[cargo-layout](./cargo/layout.png)

---

Development: New project
========================

Crate a rust project to be distributed as binary executable (DEFAULT):

```bash
 $ cargo new hello_world --bin
```

Crate a rust project to be distributed as library:

```bash
 $ cargo new hello_world --lib
```

@img[cargo-new](./cargo/cargo-binary-new.png)

+++

Development: Execute
====================

```bash
$ cargo run
   Compiling hello_world v0.1.0 (file:///path/to/package/hello_world)
     Running `target/debug/hello_world`
Hello, world!
```

---

Dependency: Versions
====================

Cargo uses semver version convention - **< major >.< minor >.< patch >**

* **patch version** to be bumped up for bug fixes that do not alter
the user facing interface, like APIs.
* **minor version** to be bumped up for backward compatible changes
to APIs.
* **major version** to be bumped up for backward in-compatible changes.

And dependency versioning uses 3 formats to identify the
maximum available, greedy, version for the build.

* Caret requirements, default requirement.
* Tilde requirements.
* Wildcard requirements.

The versioning requirements mostly matters when using "cargo update"
command.

---

Dependency: Caret requirement
==============================

![CARET](./cargo/caret-dependency.png)

Cargo considers 0.x.y to be compatible with 0.x.z, where y ≥ z and x > 0.

---

Dependency: Tilde requirement
=============================

![CARET](./cargo/caret-dependency.png)

---

Dependency: Wildcard requirement
================================

![CARET](./cargo/wildcard-dependency.png)

As of January 22nd, 2016, crates.io rejects all packages
(not just libraries) with wildcard dependency constraints.

---

Dependency: Other formats
=========================

**Inequality requirements**

![CARET](./cargo/inequality-dependency.png)

**Multiple requirements**

![CARET](./cargo/multiple-dependency.png)

---

Build
=====

To build a project:

```bash
$ cargo build
   Compiling hello_world v0.1.0 (file:///path/to/package/hello_world)
```

This builds the project in development mode, fast compilation, but
slow performing artifacts.

To build in release mode:

```bash
$ cargo build --release
   Compiling hello_world v0.1.0 (file:///path/to/package/hello_world)
```

---

Build: Cargo.lock
=================

Cargo.lock file is generated as part of the build process. Unlike the
`cargo.toml` manifest which is edited by user, `cargo.lock` is auto
generated locking down various dependencies and its exact version.

For library packages, that other packages will depend on, put Cargo.lock
in your .gitignore. In other ways libraries only specify semver
requirements for their dependencies.

For binary executables or an application, check Cargo.lock into git. In
other words, repeatable builds are guaranteed for binaries.

---

Build: Dependencies
===================

Dependencies can come from:

* Default registry crates.io, also the default dependency source.
* Git repository (via git-url).
* Local file-system.

---

Build: Git repository
=====================

---

Build: Documentation
====================

Automatically generate user-documentation using cargo:

```bash
cargo doc
```

This will create a document directory under the ``targer-dir``. To open
the documentation in browser:

```bash
cargo doc --open
```


---

Tests
=====

```bash
$ cargo test foo # This will run any test with foo in its name.

   Compiling rand v0.1.0 (https://github.com/rust-lang-nursery/rand.git#9f35b8e)
   Compiling hello_world v0.1.0 (file:///path/to/package/hello_world)
     Running target/test/hello_world-9c2b65bbb79eabce

running 0 tests

test result: ok. 0 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
```

Cargo will look for tests in two places:

1. In each of the src/ directory, typically used in unit-testing.
2. Any tests in tests/ directory, typically used in functional/integration testing.
   * Each test inside tests/ directory is a separate crate.

---

Tests: Attributes
=================

* #[test]
* #[ignore]
* #[should_panic]
@ #[cfg(test)]

---

Tests: Cargo options
====================

Options come after ``--``:

```bash
cargo test -- --nocapture
cargo test -- --ignored
cargo test -- --test-threads <n>
```


---

Distribute
==========

**crates.io** is the Rust community's central package registry that
serves as a location to discover and download packages.

---

Manifest: Package definition
============================

```toml
[package]
name = "hello_world"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
```

---

Cargo: profiles
===============

To ease cargo usage during multiple phases of development and
distribution, each phase is identified as a profile which enables
uses set of default configurations.

* **development** profile, ``[profile.dev]`` used with ``cargo build``.
* **test** profile, ``[profile.test]`` used with ``cargo test``.
* **bench** profile, ``[profile.bench]`` used with ``cargo test --release`` and ``cargo bench``.
* **release** profile, ``[profile.release]`` used with ``cargo build --release``.

---

Cargo: Configuration
====================

* target_dir

---

Cargo: airplan mode
===================

After the first time build, cargo caches all the dependencies and
typically should not access the network. To ensure that local
environment can build without network dependencies use the ``--frozen``
switch.

---

Manifest: Dependencies
======================

In the cargo.toml file:

```bash
[dependencies]
time = "0.1.12"
regex = "0.1.41"
```

Above example adds a dependency of the `time` crate and `regex` crate.
To update to newer version within the `semver` semantics:

```bash
$cargo update
```

