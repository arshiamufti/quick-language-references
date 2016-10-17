Scala's **mutable** [Stack](http://www.scala-lang.org/api/current/index.html#scala.collection.mutable.Stack) class. You don't want the immutable version. Just use `List`.

**Create a Stack just like a Seq**
```scala
scala> val stack = Stack[Int]()
stack: scala.collection.mutable.Stack[Int] = Stack()
```
* **`push`**, **`pushAll`**
```scala
scala> stack.push(10)
res0: stack.type = Stack(10)

scala> stack.push(20, 30, 40)
res1: stack.type = Stack(40, 30, 20, 10)

scala> stack.pushAll(List(50, 60))
res2: stack.type = Stack(60, 50, 40, 30, 20, 10)
```
* **`pop` removes the top element from the stack and returns it**
```scala
scala> stack.pop
res3: Int = 60
```
* **`head` or `top` returns the top element of the stack (peek)**
```scala
scala> stack.top
res4: Int = 50

scala> stack.head
res5: Int = 50
```
* **Mutate the stack just like an array**
```scala
scala> stack
res6: scala.collection.mutable.Stack[Int] = Stack(50, 40, 30, 20, 10)

scala> stack(0) = 500

scala> stack
res7: scala.collection.mutable.Stack[Int] = Stack(500, 40, 30, 20, 10)
```

* **min and max (inherited from `Seq`)**
```scala
scala> stack.min
res8: Int = 10

scala> stack.max
res9: Int = 500
```
* **`clear` removes all the elements from the stack. Why wasn't this called `popAll`, I dunno.**
```scala
scala> stack.clear

scala> stack
res10: scala.collection.mutable.Stack[Int] = Stack()
```
