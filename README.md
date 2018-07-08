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
* Design Goal - elliminate as much of {} as possible.  Similar if else syntax to go, also look at Quorum for insperation
* Provide helper parsing libraries that encourage safety and performance (interesting paper on parsing in the [rust language](https://blog.acolyer.org/2017/08/15/writing-parsers-like-it-is-2017/)
* Want to provide as close to C performance as possible for TLS
* Built in reference counting for heap allocated memory (not sure that I want to have to implement garbage collection)
* Escape analysis similar to Go for memory allocations, i.e. does a memory structure need reference counting or not?  Go uses this to figure out if something should be heap allocated or stack allocated.
* Strongly typed
  * Been looking at Dependently typed langauges, and there are some interesting ideas, but I'm currently unsure how to apply those ideas to a non-functional language.
  * One interesting thing I noticed when looking at defining methods in functional languages.  You can at compile time determine which methods should be invoked by looking at the type information.  This probably is not a performance improvement, since you can do the same with method overloading in imperitive languages, but it did make for a very concise declaration.
* Generics
* val and var syntax for variable declarations
* Type inference
* A flowable equivalent to [RxJava](http://reactivex.io/RxJava/2.x/javadoc/io/reactivex/Flowable.html) (I've been using co-routines more recently, and they seem to solve the problem that RxJava was intended to solve as well, but in a more elegant way, and with a smaller learning curve.)
* Want to be able to support zero copy parsing
* Goal is to be a 'memory safe' language
* Currying built in
* Modular linking - goal here is to allow different libraries that have the same dependencies, but at different versions, to be used in the same project.
  * Might mean needing a different linker that has a better solution for resolving dependencies than what is currently the norm.
  * How might one defend against dependency hell
  * This would need to take into account not only the version of the library the project depends on, but also the arch (x86, wasm, arm, any, etc)
    * How would this structure support something like SIMD instructions which are not always supported on every platform (for example, wasm does not yet support SIMD instructions.  This could maybe be solved by looking for the library for your target arch, and then falling back to the `any` arch if a arch specific one did not exist.  Will need to consider this more.)
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
  * It seems that there is an [opinion](https://markfaction.wordpress.com/2012/07/15/stack-based-vs-register-based-virtual-machine-architecture-and-the-dalvik-vm/) that Virtual Machines implemented using Registers performs more quickly
* Not sure that Garbage collection should be implemented or if reference counting should be used instead
* Want to mimic co-routines from Go and Kotlin, but unsure how that will affect wanting to be directly callable from C/C++ code.  The biggest question here is should the co-routine implementation be stack or offstack based.
* How exactly should modules be declared, and linked together?
* How important is ASLR protections in a 'Safe' langage?  As far as I know, ~~[GO lang does not implement this](https://rain-1.github.io/golang-aslr.html)~~ this was added as an optional feature in 1.6, it has been suggested for Rust and seems to have been [implemented recently](https://github.com/rust-lang/rust/issues/15179)
* What is stack safe?  Is this used to help prevent stack smashing?
* What all can be taken away from category theory and applied to a 'non-academic' language [category-theory](https://github.com/hmemcpy/milewski-ctfp-pdf)
* Is there a way that Guards could be built into the langauge?
  * How would they function?  Throw an exception?  If so, why not a stdlib instead of built into the language.
