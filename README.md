Language Ideas
==============

The purpose of this repo is to collect ideas for a, to be named,
computer programming language.

Target Use Cases
================
* Web applications
* Databases
* Game programming
* Native GUI applications
* Replacements for OS modules (need to define this better)
* Target browsers with a web assembly backend?

Ideas
=====

* "Local variables can be used only after they have been initialized; this is enforced by the compiler." [Idea taken from Rust](https://doc.rust-lang.org/beta/reference/variables.html) (Look at the bottom of the page for the sentence)
* Directly callable from C/C++
* Can directly call into C/C++ (FFI?)
* Automatic bounds checking
* Provide helper parsing libraries that encourage safety and performance (interesting paper on parsing in the [rust language](https://blog.acolyer.org/2017/08/15/writing-parsers-like-it-is-2017/)
* Want to provide as close to C performance as possible for TLS
* Built in reference counting for heap allocated memory (not sure that I want to have to implement garbage collection)
* Escape analysis similar to Go for memory allocations, i.e. does a memory structure need reference counting or not?  Go uses this to figure out if something should be heap allocated or stack allocated.
* Strongly typed
* Generics
* val and var syntax for variable declarations
* Type inference
* A flowable equivalent to [RxJava](http://reactivex.io/RxJava/2.x/javadoc/io/reactivex/Flowable.html)
* Want to be able to support zero copy parsing
* Goal is to be a 'memory safe' language
* Currying built in
* Modular linking - goal here is to allow different libraries that have the same dependencies, but at different versions, to be used in the same project.
* Static and dynamic linking
* Built in support for a debugger
* Built in compiler support to detect use after free bugs
* String literal interpolation
* Nullability built into the type system (similar to kotlin in this respect)
* Method chaining with the `|` operator is an interesting idea (saw this in elm with the `|>` operator.)  This seems to help cleanup wrapped functions calls by allowing you to unwind the calls.
* Bit Mapping operations built into the language.  The Goal here would be to help protocol developers to ease the transition away from C based methods, to a new method providing direct mappings to bit offsets in byte blocks that automatically implements the mapping and shift operation.  Basically, the idea here is to allow a developer to specify the structure of the byte block and have it spit out the values for the implementer reducing the chances for errors, and improving a developer's efficiency. 

Questions
=========
* Register or Stack based function calls?  (Not sure it matters if we're optimizing for fewest clock cycles vs optimal register allocation in the assembly generation) (this seems to depend on the architecture of the instruction set and os.  Need to do more research to better understand)
* Not sure that Garbage collection should be implemented or if reference counting should be used instead
* Want to mimic co-routines from Go and Kotlin, but unsure how that will affect wanting to be directly callable from C/C++ code.  The biggest question here is should the co-routine implementation be stack or offstack based.
* How exactly should modules be declared, and linked together?
* How important is ASLR protections in a 'Safe' langage?  As far as I know, [GO lang does not implement this](https://rain-1.github.io/golang-aslr.html), it has been suggested for Rust and seems to have been [implemented recently](https://github.com/rust-lang/rust/issues/15179)
* What is stack safe?  Is this used to help prevent stack smashing?
* What all can be taken away from category theory and applied to a 'non-academic' language [category-theory](https://github.com/hmemcpy/milewski-ctfp-pdf)
