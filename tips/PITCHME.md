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
