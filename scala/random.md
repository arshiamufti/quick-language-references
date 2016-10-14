### Generating random numbers

Scala's [Random](http://www.scala-lang.org/api/current/index.html#scala.util.Random) class.

```scala
scala> import scala.util.Random
import scala.util.Random

scala> val rand = new Random
rand: scala.util.Random = scala.util.Random@59c7cff
```

**Get any random integer**

```scala
scala> rand.nextInt
res86: Int = -925684131
```
**Get a random integer between 0 and 9**
```scala
scala> rand.nextInt(10)
res87: Int = 4
```

**Get a random integer from the range [10, 30]**
```scala
scala> val range = 10 to 30
range: scala.collection.immutable.Range.Inclusive = Range(10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30)

scala> range(rand.nextInt(range.length))
res88: Int = 24
```
