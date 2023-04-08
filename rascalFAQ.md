# Rascal FAQ

- how do I find a class whose names matches a string in a list of URIs?

- Where is the m3 model defined?
	- analysis::m3::Core and lang::java::m3::Core in src/org/rascalmpl/library
- How do I profile Rascal code?
	- :set profiling true
- How do I navigate from a project uri in Rascal to the files it contains?
	Locations have an ls field, so you could type something like
	|project://p2-SnakesAndLadders|.ls
	You can then use functions isFile and isDirectory
	In util::FileSystem there exists also a function, crawl, to construct an in memory model of the file system.
- How do I benchmark code?
	- see util::Benchmark
- How do I reverse a relation?
	- invert(r)
- How can I construct a location uri from a string and vv?
	- uri = ...
	- |<uri.scheme>://<uri.authority><uri.path>|
- Is visit(){} part of the language or a module?
	- It's a built-in
- How can I query just the type of an expression? (and not get its value)
	- import Type; typeOf(expr);
- How do I run the tests of just one module?
	- not yet possible
- how do I print stuff to a new window?
	- text(...);
- Where is the "text" function?
	- util::ValueUI
- How do I load a model of a Java system?
	import lang::java::m3::JDT;
	import lang::java::m3::JavaM3;
	M3 snakes = createM3FromProject(|project://p2-SnakesAndLadders|);
- How do I extend a data type, eg RunTimeException with TestFailure?
	- see lang::java::m3::JavaM3; for an example (Modifiers)
- What is the capitalization convention?
	- classes and types are capitalized
- What does := do?
	- pattern match
- What does f(x = x) do?
	eg. M3 model = createM3FromFile(f, javaVersion = javaVersion);
	- sets the default value of a function argument
- How do I write unit tests in Rascal?
	- use the "test" modifier
- How do you run Rascal programs in the eclipse environment?
	- New>Other>Rascal File
- Why does [1..5] = [1,2,3,4]?
	- Convenience. Lists usually start at zero.
- How do I concatenate ints and strings?
	- Use "<N> ..." syntax to inject N
- Should rascal modules be organized into folders just like java packages?
	- yep

---
