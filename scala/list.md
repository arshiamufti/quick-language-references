Scala's immmutable [List](http://www.scala-lang.org/api/current/index.html#scala.collection.immutable.List) class. Useful for when you need last-in-first-out access. If you want random access or first-in-first-out, use something else like an Array or Queue.

### Creating Lists

* **Using the `cons` operator**
```scala
scala>  val lst = 1 :: 3 :: 5 :: Nil
lst: List[Int] = List(1, 3, 5)
```

* **The Java way**
```scala
scala> val lst = List(1, 3, 5)
lst: List[Int] = List(1, 3, 5)
```

* **Using ranges**
```scala
scala> val lst = List.range(1, 5)
lst: List[Int] = List(1, 2, 3, 4)

scala> val lst = List.range(1, 10, 2) // 2 is the "step"
lst: List[Int] = List(1, 3, 5, 7, 9)
```

Also see [ranges](ranges.md) in Scala.

### Prepending, appending, concatenating

```scala
scala> 0 +: lst
res49: List[Int] = List(0, 1, 3, 5, 7, 9) // prepend element

scala> lst :+ 11
res50: List[Int] = List(1, 3, 5, 7, 9, 11) // append element

scala> List(-1, -2, -3) ++ lst
res51: List[Int] = List(-1, -2, -3, 1, 3, 5, 7, 9) // append lists
```

### **Cute little useful functions**
* `isEmpty` tests if the list is empty. `nonEmpty` tests if it isn't empty
* `mkString` converts the list to a string
* `contains(a)` tests if the list contains `a`.
```scala
scala> lst
res68: List[Int] = List(1, 3, 5, 7, 9)

scala> lst contains 1
res52: Boolean = true
```
* `containsSlice(l)` tests if the list contains the slice `l`.
```scala
scala> lst
res68: List[Int] = List(1, 3, 5, 7, 9)

scala> lst containsSlice List(3, 5, 7)
res53: Boolean = true
scala> lst containsSlice List(3, 5, 10)
res54: Boolean = false
```
* `distinct` returns the list with duplicate elements removed
* `reverse` reverses the list
* `count(p)` counts the number of elements in the list that satisfy the predicate `p`
* `sum` sums up the elements in the list, `product` multiplies them
* `padTo(len, elem)` appends `elem` to the list until the length `len` is achieved
* `exists(p)` tests if at **least one** element of the list satisfies the predicate `p`
* `forall(p)` tests if **all** elements of the list satisfy the predicate `p`
* `startsWith(l)` tests if the list starts with the `l`. It can also take an additional `Int` field, the index to start comparing from.
```scala
scala> lst
res68: List[Int] = List(1, 3, 5, 7, 9)

scala> lst.startsWith(List(1, 3))
res69: Boolean = true

scala> lst.startsWith(List(5, 7), 2)
res70: Boolean = true
```
* `partition(p: (A) ⇒ Boolean): (List[A], List[A])` returns a pair of lists. The first contains elements that satisfy the predicate `p` and the second contains those that don't. Relative ordering is maintained
* **`groupBy`**
```scala
def groupBy [K] (f: (A) ⇒ K): Map[K, Traversable[A]]
```
The `groupBy` function takes in a function `f`, called the **discriminator** function. `groupBy` acts on a `List[A]`. `f` is applied to each element to return something of type `K`, and the result is a map in which elements of the list are grouped by the return value of `f`. In other words, the elements of the list are **grouped by** `f`.
```scala
scala> val books = List("Anne of Green Gables", "A Wrinkle in Time", "Heidi", "A Little Princess", "Harry Potter")
books: List[String] = List(Anne of Green Gables, A Wrinkle in Time, Heidi, A Little Princess, Harry Potter)

scala> books.groupBy(_.charAt(0))
res28: scala.collection.immutable.Map[Char,List[String]] = Map(A -> List(Anne of Green Gables, A Wrinkle in Time, A Little Princess), H -> List(Heidi, Harry Potter))

scala> books.groupBy(_.size)
res29: scala.collection.immutable.Map[Int,List[String]] = Map(17 -> List(A Wrinkle in Time, A Little Princess), 20 -> List(Anne of Green Gables), 5 -> List(Heidi), 12 -> List(Harry Potter))

scala> List(1, 2, 3, 4, 5, 6, 7).groupBy {
     | case even if (even % 2 == 0) => "even"
     | case _ => "odd"
     | }
res32: scala.collection.immutable.Map[String,List[Int]] = Map(odd -> List(1, 3, 5, 7), even -> List(2, 4, 6))
```
* `permutations` returns an iterator over all the permutations of the list that you can `map` or `foreach` over, etc.

### **Return certain parts of the list**
* `head` returns the first element
* `tail` returns all elements except the first
* `init` returns all elements except the last
* `drop(i)` drops the **first** `i` elements. `dropRight(i)` drops the **last** `i` elements.
* `take(i)` takes the **first** `i` elements. `takeRight(i)` takes the **last** `i` elements.
* `find(p)` returns the first element of the list (an `Option` type) that satisfies the predicate `p`.
* `min` and `max` return the smallest and largest element respectively.

### Sorting
* `sorted` sorts the list
* `sortWith(lt: (A, A) ⇒ Boolean): List[A]` sorts the list according to `lt`, the comparison function which tests whether its first argument precedes its second argument in the desired ordering.

Also see functional combinators.

