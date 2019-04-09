core
    alloc		Memory allocation APIs
  * arch		SIMD and vendor intrinsics module.
    hint		Hints to compiler that affects how code should be emitted or optimized.
    marker		Primitive traits and types representing basic properties of types.
    mem			Basic functions for dealing with memory.
  * panic		Panic support in the standard library.

types
	char		A character type.
	convert	    Traits for conversions between types.
	f32	        This module provides constants which are specific to the
	f64	        This module provides constants which are specific to the
	i128		The 128-bit signed integer type.
	i16			The 16-bit signed integer type.
	i32			The 32-bit signed integer type.
	i64			The 64-bit signed integer type.
	i8			The 8-bit signed integer type.
				implementation of the f32 floating point data type.
			    implementation of the f64 floating point data type.
	isize		The pointer-sized signed integer type.
	option		Optional values.
	pin			Types which pin data to its location in memory
	ptr			Manually manage memory through raw pointers.
	rc			Single-threaded reference-counting pointers. 'Rc' stands for 'Reference Counted'.
	result		Error handling with the Result type.
	slice		A dynamically-sized view into a contiguous sequence, [T].
	sync		Useful synchronization primitives.
	u128		The 128-bit unsigned integer type.
	u16			The 16-bit unsigned integer type.
	u32			The 32-bit unsigned integer type.
	u64			The 64-bit unsigned integer type.
	u8			The 8-bit unsigned integer type.
	usize		The pointer-sized unsigned integer type.

behaviours
	any			This module implements the Any trait, which enables
	borrow		A module for working with borrowed data.
	boxed		A pointer type for heap allocation.
	cell		Shareable mutable containers.
	clone		The Clone trait for types that cannot be 'implicitly copied'.
	cmp			Functionality for ordering and comparison.
	default	    The Default trait for types which may have meaningful default values.
			    dynamic typing of any 'static type through runtime reflection.
	error	    Traits for working with Errors.
	iter		Composable external iteration.
	ops			Overloadable operators.

collection
	ascii		Operations on ASCII strings and characters.
	collections	Collection types.
	string		A UTF-8 encoded, growable string.
	str			Unicode string slices.
	vec			A contiguous growable array type with heap-allocated contents, written Vec<T>.

OS
	env	        Inspection and manipulation of the process's environment.
	fs	        Filesystem manipulation operations.
	io			Traits, helpers, and type definitions for core I/O functionality.
	net			Networking primitives for TCP/UDP communication.
	os			OS-specific functionality.
	path		Cross-platform path manipulation.
	process		A module for working with processes.
	thread		Native threads.

utilities
	ffi	        Utilities related to FFI bindings.
	fmt	        Utilities for formatting and printing Strings.
	hash		Generic hashing support.
	num			Additional functionality for numerics.
	time		Temporal quantification.

future		[Experimental] Asynchronous values.
intrinsics	[Experimental] rustc compiler intrinsics.
raw			[Experimental] Contains struct definitions for the layout of compiler built-in types.
task		[Experimental] Types and Traits for working with asynchronous tasks.
prelude		The Rust Prelude.
