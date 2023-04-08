# Rascal FAQ

[Rascal](https://www.cwi.nl/en/results/software/rascal-one-stop-shop-for-metaprogramming/) is a meta-programming language.
This FAQ dates from an extened site visit in Autumn 2013.

## Q Where is the m3 model defined?

`analysis::m3::Core` and `lang::java::m3::Core in src/org/rascalmpl/library`

## Q How do I profile Rascal code?
```
:set profiling true
```

## Q How do I navigate from a project uri in Rascal to the files it contains?

Locations have an ls field, so you could type something like
```
|project://p2-SnakesAndLadders|.ls
```
You can then use functions `isFile` and `isDirectory`.
In `util::FileSystem` there exists also a function, `crawl`, to construct an in memory model of the file system.

## Q How do I benchmark code?
See `util::Benchmark`

## Q How do I reverse a relation?
`invert(r)`

## Q How can I construct a location uri from a string and vv?
```
uri = ...
|<uri.scheme>://<uri.authority><uri.path>|
```

## Q Is visit(){} part of the language or a module?
It's a built-in

## Q How can I query just the type of an expression? (and not get its value)
```
import Type; typeOf(expr);
```

## Q How do I run the tests of just one module?
Not yet possible.

## Q How do I print stuff to a new window?
```
text(...);
```

## Q Where is the "text" function?
```
util::ValueUI
```

## Q How do I load a model of a Java system?
```
import lang::java::m3::JDT;
import lang::java::m3::JavaM3;
M3 snakes = createM3FromProject(|project://p2-SnakesAndLadders|);
```

## Q How do I extend a data type, eg RunTimeException with TestFailure?
See `lang::java::m3::JavaM3;` for an example (Modifiers).

## Q What is the capitalization convention?
Classes and types are capitalized.

## Q What does := do?
Pattern match.

## Q What does f(x = x) do?
E.g. `M3 model = createM3FromFile(f, javaVersion = javaVersion);`
sets the default value of a function argument.

## Q How do I write unit tests in Rascal?
Use the `test` modifier

## Q How do you run Rascal programs in the eclipse environment?
```
New>Other>Rascal File
```

## Q Why does `[1..5] = [1,2,3,4]`?
Convenience. Lists usually start at zero.

## Q How do I concatenate ints and strings?
Use `<N> ...` syntax to inject N

## Q Should Rascal modules be organized into folders just like Java packages?
Yep.

---
