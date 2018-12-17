@title[Traits]

@snap[midpoint slide1 span-80]
<h1>Traits</h1>
behaviour abstractions
@snapend


@snap[south-east author-box]
@fa[envelope](prataprc@gmail.com - R Pratap Chakravarthy) <br/>
@snapend

---

Conversion between types
========================


* **AsMut** A cheap, mutable reference-to-mutable reference conversion.
* **AsRef** A cheap reference-to-reference conversion. Used to convert a value to a reference value within generic code.
* **From** Simple and safe type conversions in to Self. It is the reciprocal of Into.
* **Into** A conversion that consumes self, which may or may not be expensive. The reciprocal of From.
* **TryFrom** [Experimental] Attempt to construct Self via a conversion.
* **TryInto** [Experimental] An attempted conversion that consumes self, which may or may not be expensive.

The key difference between the AsRef and Borrow, is the intention:

* Use AsRef when the goal is to simply convert into a reference.
* Use Borrow when the goal is related to writing code that is
agnostic to the type of borrow and whether it is a reference or value.

AsMut auto-dereferences if the inner type is a mutable reference
(e.g.: foo.as_mut() will work the same if foo has type &mut Foo or &mut &mut Foo)

---

Coercion traits
===============

Deref, DerefMut, Unsize, CoerceUnsized
