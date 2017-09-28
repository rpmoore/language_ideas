Language Ideas
==============

The purpose of this repo is to collect ideas for a, to be named,
computer programming language.

Ideas
=====

* "Local variables can be used only after they have been initialized; this is enforced by the compiler." [Idea taken from Rust](https://doc.rust-lang.org/beta/reference/variables.html) (Look at the bottom of the page for the sentence)
* Directly callable from C/C++
* Can directly call into C/C++
* Automatic bounds checking
* Provide helper parsing libraries that encourage safety and performance
* Want to provide as close to C performance as possible for TLS
* Built in reference counting for heap allocated memory
* Escape analisys similar to GO for memory allocations
* Strongly typed
* Generics
* val and var syntax for variable declarations
* A flowable equivalent to [RxJava](http://reactivex.io/RxJava/2.x/javadoc/io/reactivex/Flowable.html)
* Want to be able to support zero copy parsing
* Goal is to be a 'safe' language
* Curring built in
* Modular linking - goal here is to allow different libraries that have the same dependencies, but at different versions, to be used in the same project.
* Static and dynamic linking

Questions
=========
* Register or Stack based function calls?
* Not sure that Garbage collection should be implemented or if reference counting should be used instead
* Want to mimic co-routines from Go and Kotlin, but unsure how that will affect wanting to be directly callable from C/C++ code
* How exactly should modules be declared, and linked together?
