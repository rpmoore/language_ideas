## Dependency Resolution

Almost every software project depends on some other library to implement some of it's functionality.  With just a few dependencies, this isn't an problem.  As the project grows and more dependencies are added, the amount of dependencies can grow to be quite large, and conflicts between different versions of the same dependency can creap in.  This can wreak havok in a build system, and lead to dependency hell.

Often this is solved by pinning the dependency to a specific version.  However, this can break a dependency if version you've pinned to has changed it's interface, or even changed it's behavior.

Another issue is that many languages are not designed to deal with dependencies explicitly, and leave that as an excercise for the developer.  While this can be good in some cases, it doesn't lead to a solution that solves either of the above issues.  We propose then that a language be designed to deal with this.

To solve this, we propose the following:

* A projects dependencies will be declared internal by default.  If a library designer wants to use a dependent library in it's interface, like in the case of utility like libraries, then they must define this as a public dependency
* If a project only has internal dependencies, then when linking the program with it's dependencies, the correct version of the library will be found, and linked against.  This means that if your project has two different dependencies, each dependent on the same library, but at different versions, they will link to their version of the library.
* If a project does decide to expose a dependency in it's public interface and the versions are the same, then the consumer does not need to do anything.
* If there is a version difference in the public definition, there are a few things that could happen
  - First, if the two versions are not referenced in the same file, then the consumer has no actions to take, and the respective versions will be used [Footnote - Need to think about utility libraries for gui frameworks or for a well known library]
  - Second, if the two versions are used in the same file, then the programmer will be required to either write an explicit versioned type converter, or they can choose to annotate the transatively dependent version and ignore the conflict.  Ignoring the conflict doesn't mean that the project will successfully compile because there could be a difference in the type that cannot be resolved, but it will not error out on the conflicted types.
