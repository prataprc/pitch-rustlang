@title[Traits]

@snap[midpoint slide1 span-80]
<h1>Traits</h1>
behaviour abstractions
@snapend


@snap[south-east author-box]
@fa[envelope](prataprc@gmail.com - R Pratap Chakravarthy) <br/>
@snapend

---

Marker traits     : What are the properties of marker traits ?
Core traits       :
Operator traits   :
Conversion traits :
Auto traits       :
Unsafe-traits     :
Super traits      :

Operator traits
===============

use std::{ops, cmp};

Conversion traits
=================

Core traits
===========

Default
Display

Auto traits
===========

Opt-in, opt-out traits, built-in traits

Send
Sync
Unpin

Unsafe-traits
=============

GlobalAlloc     A memory allocator that can be registered as the standard
                library’s default though the #[global_allocator] attributes.
Alloc
Send
Sync


Super traits
============

Clone is super trait of Copy.


Others
======

Hash
CoerceUnsized

---

Conversion between types
========================


liballoc/
    ToOwned { type Owned: Borrow<Self>; }
        A generalization of Clone to borrowed data.

    SliceConcatExt<T: ?Sized> { type Output; }
        [Experimental] An extension trait for concatenating slices

    ToString
        A trait for converting a value to a String.

libcore/
    GlobalAlloc
        A memory allocator that can be registered as the standard library’s
        default though the #[global_allocator] attributes.
    Alloc
        [Experimental] An implementation of Alloc can allocate, reallocate,
        and deallocate arbitrary blocks of data described via Layout.
    Any: 'static
        A type to emulate dynamic typing.
    FixedSizeArray<T>
        [Experimental] Utility trait implemented only on arrays of fixed size

    Clone : Sized
        A common trait for the ability to explicitly duplicate an object.
    Copy : Clone
        Types whose values can be duplicated simply by copying bits.
    Send
        Types that can be transferred across thread boundaries.
    Sized
        Types with a constant size known at compile time.
    Sync
        Types for which it is safe to share references between threads.
    Unpin
        Types which can be safely moved after being pinned.
    Unsize<T: ?Sized>
        ExperimentalTypes that can be "unsized" to a dynamically-sized type.


    Borrow<Borrowed: ?Sized>

        A trait for borrowing data.

    BorrowMut<Borrowed: ?Sized> : Borrow<Borrowed> BorrowMut

        A trait for mutably borrowing data.
        Choose Borrow when you want to abstract over different kinds of
        borrowing, or when you’re building a data structure that treats
        owned and borrowed values in equivalent ways, such as hashing and
        comparison.
        Use Borrow when the goal is related to writing code that is
        agnostic to the type of borrow and whether it is a reference or value.
    AsRef<T: ?Sized>
        A cheap reference-to-reference conversion. Used to convert a value to
        a reference value within generic code.
        Choose AsRef when you want to convert something to a reference
        directly, and you’re writing generic code.
        Use AsRef when the goal is to simply convert into a reference.
        Auto-dereferences if the inner type is a mutable reference. EG:
        foo.as_mut() will work the same if foo is `&mut Foo` or `&mut &mut Foo`
    AsMut<T: ?Sized>
        A cheap, mutable reference-to-mutable reference conversion.
    Into<T>: Sized
        A conversion that consumes self, which may or may not be expensive. The
        reciprocal of From.
    From<T>: Sized
        Simple and safe type conversions in to Self. It is the reciprocal of Into.
    TryInto<T>: Sized { type Error; }
        An attempted conversion that consumes self, which may or may not be
        expensive.
    TryFrom<T>: Sized { type Error; }
        Simple and safe type conversions that may fail in a controlled way
        under some circumstances. It is the reciprocal of TryInto.
    FromStr: Sized { type Err; }
        Parse a value from a string

    Default: Sized
        A trait for giving a type a useful default value.

    PartialEq<Rhs: ?Sized = Self> {
        Trait for equality comparisons which are partial equivalence relations.
    Eq: PartialEq<Self>
        Trait for equality comparisons which are equivalence relations.
    PartialOrd<Rhs: ?Sized = Self>: PartialEq<Rhs> {
        Trait for values that can be compared for a sort-order.
    Ord: Eq + PartialOrd<Self> {
        Trait for types that form a total order.

    Add<RHS = Self> { type Output; }
        The addition operator +.
    AddAssign<Rhs = Self>
        The addition assignment operator +=.
    Sub<RHS = Self> { type Output; }
        The subtraction operator -.
    SubAssign<Rhs = Self>
        The subtraction assignment operator -=.
    Mul<RHS = Self> { type Output; }
        The multiplication operator \*.
    MulAssign<Rhs = Self>
        The multiplication assignment operator \*=.
    Div<RHS = Self> { type Output; }
        The division operator /.
    DivAssign<Rhs = Self>
        The division assignment operator /=.
    Rem<RHS = Self> { type Output = Self; }
        The remainder operator %.
    RemAssign<Rhs = Self>
        The remainder assignment operator %=.
    Neg { type Output; }
        The unary negation operator -.

    BitAnd<RHS = Self> { type Output; }
        The bitwise AND operator &.
    BitAndAssign<Rhs = Self>
    	The bitwise AND assignment operator &=.
    BitOr<RHS = Self> { type Output; }
        The bitwise OR operator |.
    BitOrAssign<Rhs = Self>
        The bitwise OR assignment operator |=.
    BitXor<RHS = Self> { type Output; }
        The bitwise XOR operator ^.
    BitXorAssign<Rhs = Self>
        The bitwise XOR assignment operator ^=.
    Shl<RHS = Self> { type Output; }
        The left shift operator <<. Note that because this trait is
        implemented for all integer types with multiple right-hand-side
        types, Rust's type checker has special handling for _ << _,
        setting the result type for integer operations to the type of the
        left-hand-side operand. This means that though a << b and a.shl(b)
        are one and the same from an evaluation standpoint, they are
        different when it comes to type inference.
    ShlAssign<Rhs = Self>
        The left shift assignment operator <<=.
    Shr<RHS = Self> { type Output; }
        The right shift operator >>. Note that because this trait is
        implemented for all integer types with multiple right-hand-side
        types, Rust's type checker has special handling for _ >> _,
        setting the result type for integer operations to the type of the
        left-hand-side operand. This means that though a >> b and a.shr(b)
        are one and the same from an evaluation standpoint, they are
        different when it comes to type inference.
    ShrAssign<Rhs = Self>
        The right shift assignment operator >>=.
    Not { type Output; }
        The unary logical negation operator !.

    RangeBounds <T: ?Sized>
        RangeBounds is implemented by Rust's built-in range types,
        produced by range syntax like .., a.., ..b or c..d.
    Index <Idx: ?Sized> { type Output: ?Sized; }
        Used for indexing operations (container[index]) in immutable
        contexts.
    IndexMut <Idx: ?Sized>: Index<Idx>
        Used for indexing operations (container[index]) in mutable
        contexts.
    Try { type Ok; type Error; }
        [Experimental] A trait for customizing the behavior of ?  operator.

    Deref { type Target: ?Sized; }
        Used for immutable dereferencing operations, like \*v.
    DerefMut: Deref
        Used for mutable dereferencing operations, like in \*v = 1;.
    Drop
        Used to run some code when a value goes out of scope.
        This is sometimes called a 'destructor'.

    FnMut<Args>: FnOnce<Args>
        The version of the call operator that takes a mutable receiver.
    Fn<Args>: FnMut<Args>
        The version of the call operator that takes an immutable receiver.
    FnOnce<Args> { type Output; }
        The version of the call operator that takes a by-value receiver.
    FnBox<A> { type Output; }
        [Experimental] FnBox is a version of the FnOnce intended for use
        with boxed closure objects. The idea is that where one would normally
        store a Box<dyn FnOnce()> in a data structure, you should use
        Box<dyn FnBox()>. The two traits behave essentially the same, except
        that a FnBox closure can only be called if it is boxed. (Note that
        FnBox may be deprecated in the future if Box<dyn FnOnce()> closures
        become directly usable.)

    Binary      b formatting.
    Debug       ? formatting.
    Display     Format trait for an empty format, {}.
    LowerExp    e formatting.
    LowerHex    x formatting.
    Octal       o formatting.
    Pointer     p formatting.
    UpperExp    E formatting.
    UpperHex    X formatting.
    Write
        Collection of methods that are required to format a message
        into a stream.

    Future
        [Experimental] A future represents an asynchronous computation.
    Hash
        A hashable type.
        Types implementing Hash can be hashed with an instance of Hasher.
    Hasher
        A trait for hashing an arbitrary stream of bytes.
    BuildHasher { type Hasher: Hasher; }
        A trait for creating instances of Hasher.

    Sum<A = Self>: Sized
    Product<A = Self>: Sized
    FromIterator<A>: Sized
    IntoIterator
    Extend<A>
    Iterator
    FusedIterator: Iterator
    TrustedLen : Iterator
    ExactSizeIterator: Iterator
    DoubleEndedIterator: Iterator
    Step: Clone + PartialOrd + Sized
    TrustedRandomAccess : ExactSizeIterator
    TrustedRandomAccess : ExactSizeIterator
    Freeze
    DecodableFloat: RawFloat + Copy
    FullOps: Sized
    Drop
    FnBox<A>: FnOnce<A>
    CoerceUnsized<T: ?Sized>
    DispatchFromDyn<T>
    Deref
    DerefMut: Deref
    Receiver
    Generator
    BoxMeUp
    Sealed
    SliceIndex<T: ?Sized>: private_slice_index::Sealed
    Pattern<'a>: Sized
    Searcher<'a>
    ReverseSearcher<'a>: Searcher<'a>
    DoubleEndedSearcher<'a>: ReverseSearcher<'a>

libgraphviz/
    Labeller<'a>
    GraphWalk<'a>

libproc_macro/
    ApplyL<'a>
    LambdaL: for<'a> ApplyL<'a>
    Encode<S>: Sized
    Decode<'a, 's, S>: Sized
    DecodeMut<'a, 's, S>: Sized
    trait Types
    $(pub trait $name: Types
    Server: Types $(+ $name)*
    DispatcherTrait
    ExecutionStrategy
    MultiSpan

libserialize/
    ToHex
    FromHex
    ToJson
    Encoder
    Decoder
    Encodable
    Decodable: Sized
    SpecializationError
    SpecializedEncoder<T: ?Sized + UseSpecializedEncodable>: Encoder
    SpecializedDecoder<T: UseSpecializedDecodable>: Decoder
    UseSpecializedEncodable
    UseSpecializedDecodable: Sized

libstd/
    AsciiExt
    AsInner<Inner: ?Sized>
    AsInnerMut<Inner: ?Sized>
    AsRawFd
    AsRawHandle
    AsRawSocket
    BufRead: Read
    CommandExt
    DirBuilderExt
    DirEntryExt
    Error: Debug + Display
    ExitStatusExt
    FileExt
    FileTypeExt
    FromInner<Inner>
    FromRawFd
    FromRawHandle
    FromRawSocket
    IntoInner<Inner>
    IntoRawFd
    IntoRawHandle
    IntoRawSocket
    IsMinusOne
    IsZero
    JoinHandleExt
    JoinHandleExt
    MetadataExt
    OpenOptionsExt
    OsStrExt
    OsStringExt
    Packet
    PermissionsExt
    Put<K, V>
    Read
    RefUnwindSafe
    Seek
    Termination
    ToSocketAddrs
    TryIntoInner<Inner>: Sized
    TryIntoRawFd: Sized
    UnwindSafe
    UserSafe
    UserSafeSized: Copy + Sized
    Write

libsyntax/
    HasAttrs: Sized
    MultiItemDecorator
    MultiItemModifier
    ProcMacro
    AttrProcMacro
    TTMacroExpander
    IdentMacroExpander
    MacResult
    Resolver
    AstBuilder
    ExpectOne<A: Array>
    MutVisitor: Sized
    PpAnn
    PrintState<'a>
    FileLoader
    MapInPlace<T>: Sized
    Visitor<'ast>: Sized

libterm/
    Terminal: Write

libtest/
    OutputFormatter
    TDynBenchFn: Send
    Stats
