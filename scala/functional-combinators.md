* [map](#map)
* [foreach](#foreach)
* [filter](#filter)
* [zip, zipAll, zipWithIndex](#zip)
* [foldLeft](#foldleft)
* [foldRight](#foldright)
* [flatten](#flatten)
* [flatMap](#flatmap)
* [reduceLeft, reduceRight](#reduceleft-reduceright)
* [drop, dropWhile](#drop-and-dropwhile)

### map
```scala
map[B](f: (A) ⇒ B): List[B]
```
Evaluates a function over each element in the list, returning a list with the same number of elements. The parameter `f` can be a lambda (anonymous function)

```scala
scala> val numbers = List(1, 2, 3, 4)
numbers: List[Int] = List(1, 2, 3, 4)

scala> numbers.map(i => i * 2)
res0: List[Int] = List(2, 4, 6, 8)
```
..or a function.

```scala
scala> def timesTwo(i: Int): Int = i * 2
timesTwo: (i: Int)Int

scala> numbers.map(timesTwo)
res1: List[Int] = List(2, 4, 6, 8)

scala> numbers map timesTwo // I like this
res2: List[Int] = List(2, 4, 6, 8)
```
### foreach
```scala
def foreach(f: (A) ⇒ Unit): Unit
```

I wish this was in camel case, but oh well. It's just like `map`, except the function applied to each element returns nothing (void), so use it for side effects--printing, mutating, etc.

```scala
scala> numbers foreach println
1234
```

### filter
```scala
def filter(p: (A) ⇒ Boolean): List[A]
```
Selects elements from the list which **satisfy** the predicate (a unary function returning a boolean). There's also `filterNot`, which does the opposite: selects elements from the list which do **not** satisfy the given predicate.

### zip
```scala
def zip[B](that: GenIterable[B]): List[(A, B)]
```
* Takes in an iterable collection `that` (a list, array, etc) and returns a new list of pairs, combining corresponding elements in pairs.
* Length of the new list is the minimum of the length of the two lists.
* If you want the resulting list to be the longer of the who, use [zipAll](http://www.scala-lang.org/api/current/index.html#scala.collection.immutable.List@zipAll[B](that:Iterable[B],thisElem:A,thatElem:B):List[(A,B)]) and specify placeholder elements to fill up the resulting list if either one is shorter.

```scala
scala> List("a", "an", "the") zip List("bat", "apple", "tree", "book")
res0: List[(String, String)] = List((a,bat), (an,apple), (the,tree))
```
* Use `zipWithIndex` to obtain a new list containing pairs consisting of all elements of this list paired with their index. Indices start at 0.

```scala
scala> List("a", "an", "the").zipWithIndex
res0: List[(String, Int)] = List((a,0), (an,1), (the,2))
```

### foldLeft
```scala
def foldLeft[B](z: B)(f: (B, A) => B): B
```
* `foldLeft` goes over the list from **head** to **tail** (right to left). For the first item, the seed value `z` is used as the first parameter to `f`. For the second list item, the result of the first call to `f` is used as the `B` type parameter, and so on.
* Think of `z` as a base case, the value to be returned when the list (assuming `B` = `List[Something]`) is empty.
* As the list is traversed, the value resulting from applying `f` is "accumulated" into the `B` type parameter. When the list is empty, the accumulator is returned.
* `foldLeft` is implemented [tail recursively](https://github.com/scala/scala/blob/05016d9035ab9b1c866bd9f12fdd0491f1ea0cbb/src/library/scala/collection/LinearSeqOptimized.scala#L118) (using a while loop) so it's the better choice over `foldRight`.
* Some [code examples](https://oldfashionedsoftware.com/2009/07/30/lots-and-lots-of-foldleft-examples/) that I didn't write.

```scala
def sum(list: List[Int]): Int = list.foldLeft(0)((r,c) => r+c) // add the numbers in a list
def sum(list: List[Int]): Int = list.foldLeft(0)(_+_) // or do it the fancy scala way
def rev(list: List[Int]): List[Int] = list.foldLeft(List[Int]())((r,c) => c::r) // reverse a list
```

### foldRight
* It's like `foldLeft` except it goes over the list from the end to the beginning. Since the results of the recursive call are used for **further** calculation, the implementation of `foldRight`, although [super pretty](https://github.com/scala/scala/blob/05016d9035ab9b1c866bd9f12fdd0491f1ea0cbb/src/library/scala/collection/LinearSeqOptimized.scala#L129), is not tail recursive and we'll get stack overflows lol.
* In the scala source code for `List`, the implementation of foldRight is overriden with a nice [one line implementation](https://github.com/scala/scala/blob/2.12.x/src/library/scala/collection/immutable/List.scala#L393): reverse the list, and apply `foldLeft`.

### flatten

Use this to obatain a list from a list of lists.

```scala
scala> List(List(1,2), List(4, 5)).flatten
res0: List[Int] = List(1, 2, 4, 5)
```

### flatMap

* I've heard someone refer to `flatMap` as "mapFlat". `flatMap` **map**s over a list and then **flat**tens it.
```scala
/* taken from Twitter */
scala> val nestedNumbers = List(List(1, 2), List(3, 4), List())
nestedNumbers: List[List[Int]] = List(List(1, 2), List(3, 4), List())

scala> nestedNumbers.flatMap(x => x.map(_ * 2))
res0: List[Int] = List(2, 4, 6, 8)

// the above is equivalent to
scala> nestedNumbers.map((x: List[Int]) => x.map(_ * 2)).flatten
res1: List[Int] = List(2, 4, 6, 8)
```
* An `Option` is a container of 0 or 1 things. So a neat use of `flatMap` is
```scala
scala> def f(x: Int) = if (x > 2) Some(x*2) else None
f: (x: Int)Option[Int]

scala> val l = List(1, 2, 3, 4)
l: List[Int] = List(1, 2, 3, 4)

// say we want to apply f to each element of l. We can use a map...
scala> l map f
res2: List[Option[Int]] = List(None, None, Some(6), Some(8))

// ... and then flatten it
scala> (l map f) flatten
res3: List[Int] = List(6, 8)

// ...or use flatMap \o/ and rid of the Some's and None's in one step
scala> l flatMap f
res4: List[Int] = List(6, 8)
```

### reduceLeft, reduceRight

### collect

### for, while

### Ranges

### Partial Functions

### partition

### find

### drop and dropWhile

(took this completely from Twitter's scala school).
* `drop` drops the first `i` elements.

```scala
scala> numbers.drop(5)
res0: List[Int] = List(6, 7, 8, 9, 10)
```
* `dropWhile` removes the first elements that match a predicate function. For example, if we dropWhile odd numbers from our list of numbers, 1 gets dropped (but not 3 which is “shielded” by 2).

```scala
scala> numbers.dropWhile(_ % 2 != 0)
res0: List[Int] = List(2, 3, 4, 5, 6, 7, 8, 9, 10)
```
