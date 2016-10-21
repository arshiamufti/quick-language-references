```scala
scala> 1 to 5
res71: scala.collection.immutable.Range.Inclusive = Range(1, 2, 3, 4, 5)

scala> 1 until 5
res72: scala.collection.immutable.Range = Range(1, 2, 3, 4)

scala> 'A' to 'F'
res74: scala.collection.immutable.NumericRange.Inclusive[Char] = NumericRange(A, B, C, D, E, F)
```

**Use ranges to create other sequences**
```scala
scala> (1 to 5) toList
res78: List[Int] = List(1, 2, 3, 4, 5)

scala> (1 to 5) toArray
res79: Array[Int] = Array(1, 2, 3, 4, 5)

scala> (1 to 5) toSet
res81: scala.collection.immutable.Set[Int] = Set(5, 1, 2, 3, 4)
```

**Ways to create custom ranges**

* Step through the values using `by`
```scala
scala> 1 to 10 by 2
res73: scala.collection.immutable.Range = Range(1, 3, 5, 7, 9)
```

* Use `map`

```scala
scala> (1 to 5) map { n => n + 2 } toList
res76: List[Int] = List(3, 4, 5, 6, 7)
```
