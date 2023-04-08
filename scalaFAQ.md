# Scala FAQ

## Q How to write scripts?
```
#! /usr/bin/env scala
# save as hello.command or hello.sh or hello.scala
object HelloWorld {
  def main(args: Array[String]) {
    println("Hello, world! " + args.toList)
  }
}
HelloWorld.main(args) 
```

## Q How to package a Scala project as an executable jar?

See: http://raintomorrow.cc/post/50811498259/how-to-package-a-scala-project-into-an-executable-jar

## Q Unit tests?

- Install the ScalaTest plugin for Eclipse.
- Add JUnit to the build path of your project
- Add the (external) ScalaTest jar to the build path

## Q Debugging? Profiling? IDE?

*NB:* covariant etc discussions in Scala could be useful for the Objects and Types lecture
