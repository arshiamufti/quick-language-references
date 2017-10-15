[offical docs](https://www.scala-lang.org/api/current/scala/collection/mutable/PriorityQueue.html)


**import**

```
import scala.collection.mutable.PriorityQueue
```

**creating**

```
val maxHeap = PriorityQueue[Int]

// this creates a max heap on Ints because that's default `Ordering` on Ints (in other words, Ints are ordered in increasing order by
// default. To create a min heap, create a PriorityQueue instance, but give it the reverse `Ordering` explicitly.

val minHeap = PriorityQueue[Int].reverse
```

**add stuff**

```
maxHeap.enqueue(4)
```

**remove the highest priority element**

```
val poppedThing = maxHeap.dequeue()
```

Other stuff like `size` and `isEmpty` applies.
