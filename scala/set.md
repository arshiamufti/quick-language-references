Scala's [immutable Set](http://www.scala-lang.org/api/current/scala/collection/immutable/Set.html) class (in scope by default) and [mutable Set](http://www.scala-lang.org/api/current/scala/collection/mutable/Set.html) class. An [overview](http://docs.scala-lang.org/overviews/collections/sets.html) of Sets, SortedSets, and BitSets.

### Additions

* `xs += x`	Adds element x to set xs as a side effect and returns xs itself.
* `xs += (x, y, z)`	Adds the given elements to set xs as a side effect and returns xs itself.
* `xs ++= ys`	Adds all elements in ys to set xs as a side effect and returns xs itself.
* `xs add x`	Adds element x to xs and returns true if x was not previously contained in the set, false if it was.

### Removals

* `xs -= x`	Removes element x from set xs as a side effect and returns xs itself.
* `xs -= (x, y, z)`	Removes the given elements from set xs as a side effect and returns xs itself.
* `xs --= ys`	Removes all elements in ys from set xs as a side effect and returns xs itself.
* `xs remove x`	Removes element x from xs and returns true if x was previously contained in the set, false if it was not.
* `xs retain p`	Keeps only those elements in xs that satisfy predicate p.
* `xs.clear()`	Removes all elements from xs.

### Update

* `xs.update(x, b))` If boolean argument b is true, adds x to xs, otherwise removes x from xs.
