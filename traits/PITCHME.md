@title[Traits]

@snap[midpoint slide1 span-80]
<h1>Traits</h1>
behaviour abstractions
@snapend


@snap[south-east author-box]
@fa[envelope](prataprc@gmail.com - R Pratap Chakravarthy) <br/>
@snapend

---

Marker traits
=============

Copy    Types whose values can be duplicated simply by copying bits.
Send    Types that can be transferred across thread boundaries.
Sized   Types with a constant size known at compile time.
Sync    Types for which it is safe to share references between threads.
Unpin   Types which can be safely moved after being pinned.
Unsize  [Experimental] Types that can be "unsized" to a dynamically-sized type.

What are the properties of marker traits ?

Auto traits
===========

Opt-in, unsafe-traits, opt-out traits, built-in traits

Super traits
============

Clone is super trait of Copy.

Operator traits
===============

Add AddAssign Sub SubAssign Div DivAssign Mul MulAssign Rem RemAssign
Neg
BitAnd BitAndAssign BitOr BitOrAssign BitXor BitXorAssign
Shl ShlAssign Shr ShrAssign
Not
Index IndexMut RangeBounds
Deref DerefMut
Drop
Fn FnOnce FnMut
Try
PartialEq Eq PartialOrd Ord

Conversion traits
=================

FromStr


Others
======

Hash Default Display
Unsize CoerceUnsized

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
