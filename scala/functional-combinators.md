* [pf](##Partial Functions)

### map

### flatMap

### filter

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

## reduceLeft, reduceRight

## collect

## for, while

## zipWithIndex

## Ranges

## Partial Functions
