Scala's String class. Like Java strings, scala strings are immutable. You can also thing of strings as a `Seq[Char]`, and `map`, `filter`, `foldRight` etc over them.

For a string `S`,
* `S.length` returns length of the string in characters
```scala
scala> "asdf".length
res0: Int = 4
```
* `S.toCharArray` converts `S` to `Array[Char]`
```scala
scala> "asdf".toCharArray
res0: Array[Char] = Array(a, s, d, f)
```
* use `mkString` to convert from `Array[Char]` back to a string
```scala
scala> val charArr = Array('c', 'h', 'a', 'r')
charArr: Array[Char] = Array(c, h, a, r)

scala> charArr.mkString
res1: String = char
```
* `S.reverse` returns the string backwards
* `S.isEmpty` is the same as `S.length == 0`, `S.nonEmpty` is the same as `S.length != 0`
* Append two strings using the `+` operator.
* `S.substring(i)` returns the part of the string starting at index `i`
```scala
scala> "helloworld".substring(3)
res1: String = loworld
```
* `S.substring(i,j)` returns the part of the string **starting at index i and going up to index i-1**
```scala
scala> "helloworld".substring(3, 5)
res2: String = lo
```
* `S.contains(T)` returns `true` if `T` is a substring of `S`
```scala
scala> "helloworld".contains("ello")
res3: Boolean = true
```
* **Changing case:** `S.toLowerCase`,`S.toUpperCase`, and `S.capitalize` do exactly what you think they do.
```scala
scala> "hellowoRld".toLowerCase
res4: String = helloworld

scala> "hellowoRld".toUpperCase
res5: String = HELLOWORLD

scala> "hellowoRld".capitalize
res6: String = HellowoRld
```
* `S.startsWith(T)` returns `true` if `S` **starts** with `T` (a string). `S.endsWith(T)` returns `true` if `S` **ends** with `T`.
* **Trim whitespace**: `S.trim` returns a **copy** of the string with white space at both ends removed.
* **Split a string**: `S.split(T)` returns an `Array[String]` with `S` broken down into tokens separated by `T`
```scala
scala> "hello world".split(" ")
res7: Array[String] = Array(hello, world)

scala> val kvpairs = "key1=value1&key2=value2&key3=value3" split "&"
kvpairs: Array[String] = Array(key1=value1, key2=value2, key3=value3)

scala> kvpairs map { pair => pair.split("=") }
res8: Array[Array[String]] = Array(Array(key1, value1), Array(key2, value2), Array(key3, value3))
```
* **Replacing parts of strings**
  * `S.replace(c1, c2)` returns a new string with **all** characters `c1` replaced by `c2`
  * `S.replace(T1, T2)` returns a new string with **all** occurrences of the substring `T1` replaced by `T2`
  * `S.replaceAll(T1, T2)` returns a new string with **all** occurrences of the substring `T1` replaced by `T2`, except `T1` and `T2` are **regexes**.
* `S.matches(T)` returns `true` if `S` matches the **regex** `T`.
* **Indices**
  * `S.indexOf(T)` returns the index of the first occurrence of `T` (string **or** char) in `S` (or -1)
  * `S.indexOf(T, i)` returns the index of the first occurrence after index i of the substring T in S (or -1)
  * There's also `lastIndexOf(T)` which works just like above, but for the **last** occurence
