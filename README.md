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
* Provide helper parsing libraries that encourage safety and performance
* Want to provide as close to C performance as possible for TLS
* Built in reference counting for heap allocated memory (not sure that I want to have to implement garbage collection)
* Escape analisys similar to GO for memory allocations
* Strongly typed
* Generics
* val and var syntax for variable declarations
* Type inference
* A flowable equivalent to [RxJava](http://reactivex.io/RxJava/2.x/javadoc/io/reactivex/Flowable.html)
* Want to be able to support zero copy parsing
* Goal is to be a 'memory safe' language
* Curring built in
* Modular linking - goal here is to allow different libraries that have the same dependencies, but at different versions, to be used in the same project.
* Static and dynamic linking
* Built in support for a debugger
* Built in compiler support to detect use after free bugs
* String literal interpolation
* Nullability built into the type system (similar to kotlin in this respect)

Questions
=========
* Register or Stack based function calls?  (Not sure it matters if we're optimizing for fewest clock cycles vs optimal register allocation in the assembly generation)
* Not sure that Garbage collection should be implemented or if reference counting should be used instead
* Want to mimic co-routines from Go and Kotlin, but unsure how that will affect wanting to be directly callable from C/C++ code
* How exactly should modules be declared, and linked together?
* How important is ASLR protections in a 'Safe' langage?  As far as I know, [GO lang does not implement this](https://rain-1.github.io/golang-aslr.html), it has been suggested for Rust, but as of this writing it [hasn't been implemented](https://github.com/rust-lang/rust/issues/15179)
* What is stack safe?  Is this used to help prevent stack smashing?
