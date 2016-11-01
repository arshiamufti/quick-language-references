Scala's [immutable Map](http://www.scala-lang.org/api/current/scala/collection/immutable/Map.html) class (in scope by default). Scala's [mutable Map](http://www.scala-lang.org/api/current/scala/collection/mutable/Map.html) class which you need to import.

```scala
import scala.collection.mutable.Map
```

### Immutable Maps
All of this applies to mutable maps as well

**Accessing values**

* `m.get(k)` returns the value associated with `k` as an `Option` or `None` if it doesn't exist
* `m(k)` returns the value associated with `k` or throws an exception if not found
* `m.getOrElse(k)` returns the value associated with `k` or the default value `d` if not found
* `m.contains(k)` tests if `m` contains a mapping of the key `k`, equivalent to `isDefinedAt`

**Update**

* `m + (k -> v)`	returns the map containing all mappings of `m` plus the mapping k -> v. There's also `m + (k -> v, l -> w...)`
* `m ++ kvs` returns the map containing all mappings of ms as well as all key/value pairs of `kvs` (list of key value pairs)

**Remove**

* There's `-` equivalents for the above

**Subcollections**

* `m.keys`	returns an iterable containing each key in `m`
* `m.values`	returns an iterable containing each key in `m`

### Mutable Maps

The above functions act on mutable maps exactly like they would on an immutable map, aka they don't do any mutation or have any side effects.

Additional stuff for mutable maps.

**Create**
```scala
scala> var m = Map[Int, String]()
m: scala.collection.mutable.Map[Int,String] = Map()
```

**Update**

* `m(k) = v` adds a `k->v` mapping to `m` as a side effect, overwriting any previous mapping of `k`, returns `Unit`
```scala
scala> m(3) = "asdf"

scala> m
res1: scala.collection.mutable.Map[Int,String] = Map(3 -> asdf)
```

* `m += (k->v)` updates `m` with the `k->v` mapping, overwriting any previous mapping of `k`, returns the updated map.
  * There's also `m += (k1->v1, k2->v2..)`
  * Also `m += l` where `l` is a collection of key-value pairs
  * There's also equivalent "remove" functions (just replace the `+` with a `-`)
```scala
scala> m += (5 -> "foo")
res3: scala.collection.mutable.Map[Int,String] = Map(5 -> foo, 3 -> asdf)

scala> m ++= List((1 -> "hello"), (2 -> "world"))
res5: scala.collection.mutable.Map[Int,String] = Map(2 -> world, 5 -> foo, 1 -> hello, 3 -> asdF)
```
* `m.getOrElseUpdate(k, v)` returns `m(k)` if the mapping exists, or updates `m` with `k->v` and returns `v`.

**Remove**

* There's equivalent remove functions to the ones above (just replace the `+` with `-`)
* `m remove k` removes `k` from `m` and returns the value associated with `k`
* `m.clear` removes all mappings

**Others**

* **Sort a map**
```scala
scala> val m = Map(1->0, 3->4, 2->1)
m: scala.collection.mutable.Map[Int,Int] = Map(2 -> 1, 1 -> 0, 3 -> 4)
```

 * if you just want the keys and values sorted, not necessarily in a map, use `sortBy` or `sortWith` 
```scala
scala> m.toSeq.sortBy(_._1)
res0: Seq[(Int, Int)] = ArrayBuffer((1,0), (2,1), (3,4))

scala> m.toSeq.sortWith(_._1 > _._1)
res1: Seq[(Int, Int)] = ArrayBuffer((3,4), (2,1), (1,0))
```

 * if you want the result as a map, wrap up the result above in an **immutable** `ListMap` (dunno why it has to be immutable, but it doesn't work with a mutable one--I should look into this)
```scala
scala> import scala.collection.immutable.ListMap
import scala.collection.immutable.ListMap

scala> scala.collection.immutable.ListMap(m.toSeq.sortBy(_._1): _*)
res2: scala.collection.immutable.ListMap[Int,Int] = Map(1 -> 0, 2 -> 1, 3 -> 4)
```
