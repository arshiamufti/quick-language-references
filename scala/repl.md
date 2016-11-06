To start the scala repl,

```
My-MacBook-Pro:~ me$ scala
Welcome to Scala version 2.11.7 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_45).
Type in expressions to have them evaluated.
Type :help for more information.

scala>
```
(This is useful for quickly testing code without writing tests or a driver method)

```
scala> :load your-file.scala
Loading your-file.scala...
import scala.collection.mutable.Map  // import statements in your-file.scala
defined class SomeClass              // some class defined in your-file.scala'

scala>

// play with your-file.scala here
```
