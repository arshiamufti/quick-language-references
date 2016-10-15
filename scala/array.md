Scala's [Array](http://www.scala-lang.org/api/current/index.html#scala.Array) class.

**Create a fixed length array with the values initialized to some value**
```scala
scala> val arr = Array.fill(4)(0)
arr: Array[Int] = Array(0, 0, 0, 0)

scala> val arr = Array.fill(4)(List[Int]())
arr: Array[List[Int]] = Array(List(), List(), List(), List())
```
