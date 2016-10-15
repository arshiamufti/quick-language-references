Scala's [Array](http://www.scala-lang.org/api/current/index.html#scala.Array) class.

**Create a fixed length array**

I like using `Array.fill` since it forces you to initialize the array
```scala
scala> val arr = Array.fill(4)(0)
arr: Array[Int] = Array(0, 0, 0, 0)

scala> val arr = Array.fill(4)(List[Int]())
arr: Array[List[Int]] = Array(List(), List(), List(), List())
```
`fill` is a [curried](https://github.com/scala/scala/blob/v2.11.8/src/library/scala/Array.scala#L262) function. If you don't want to specify the initial value just yet, treat it as a partially applied function.

```scala
scala> val x = Array.fill(4)
<console>:16: error: missing arguments for method fill in object Array; // whoops

scala> val x: (=> Int) => Array[Int] = Array.fill(4)_
x: (=> Int) => Array[Int] = <function1>
```
The type of x tells us that it takes in a parameter of type `=> Int`, which is a [by-name parameter](https://tpolecat.github.io/2014/06/26/call-by-name.html) and returns an integer array. Very simply, anything of type `=>A` acts like a `def`: it's evaluated whenever it's used. (This is not the same as laziness. A `lazy val` is evaluated only **once**, when it's needed but a parameter of type `=>A` is evaluated **every time** it's needed).

And now we apply `x`!

```scala
scala> x(3) 
res1: Array[Int] = Array(3, 3, 3, 3)
```
       
...as opposed to `Array.ofDim`, which you use if you don't want to initialize the array.
```scala
scala> Array.ofDim[Double](4)
res1: Array[Double] = Array(0.0, 0.0, 0.0, 0.0)

scala> Array.ofDim[String](4)
res2: Array[String] = Array(null, null, null, null)
```
`null`s in Scala make me sad.

**Change the values in an array**

Scala arrays, like arrays in Java are fixed length, but their elements can be mutated.

```scala
scala> val numbers = Array(1, 2, 3, 4)
numbers: Array[Int] = Array(1, 2, 3, 4)

scala> numbers(3) = 0

scala> numbers
res112: Array[Int] = Array(1, 2, 3, 0)
```

```scala
scala> arr(0) = List(2, 3) // arr is now Array(List(2, 3), List(), List(), List())

// +: returns a **new** list with 9 prepended to the old one--no mutation here.
// arr(0) is then updated with this value
scala> arr(0) = 9 +: arr(0) 

scala> arr
res117: Array[List[Int]] = Array(List(9, 2, 3), List(), List(), List())
```
