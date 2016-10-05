## Stuff to note:

If your match is not exhaustive, you'll get
- a compile time warning (unless you've turned warnings off)
- a run time error if there's no match for an input

## Stuff You Can do

### Match types

```scala
def process(message : Any): String = message match {
	case x : String => s"received a string $x"
    case x: Int => s"received int $x"
    case _ => "something else"
}
```

### Use Guards

```scala
def process(message : Int): String = message match {
	case 1 | 2 | 3 => "received 1, 2, or 3"
	case 22 => "received 22"
	case x : Int if x < 0 => s"received a negative number $x"
    case _ => "received something that is not 1, 2, 3, 22 or negative"
}
```

### Alias a pattern (or part of it) using @

The alias is put before the part of the pattern, separated by @.

```scala
abstract class Location
case class Coordinates(lat: String, long: String) extends Location
case class Address(city: String, country: String) extends Location

def process(location: Location): String = location match {
    case address @ Address(_, "Canada") => s"canadian address $address"
    case address @ Address(_, _) => s"non-canadian address $address"
    case coord @ Coordinates(_, _) => s"coordinates $coord"
}
```

### Extract data using case classes

```scala
abstract class Exp

case class Sum(exp1: Exp, exp2: Exp) extends Exp  
case class Product(exp1: Exp, exp2: Exp) extends Exp  

def print(e: Exp): String = e match {
    case Sum(e1, e2) => "adding!"
    case Product(e1, e2) => "multiplying!"
}
```

To perform more powerful extractions and apply a series of pattern matching, use [Scala extractors](https://pragprog.com/magazines/2012-03/scala-for-the-intrigued).

## Examples

### Lists

```scala
def sum(list: List[Int]): Int = list match {
    case Nil => 0
    case n :: rest => n + sum(rest)
}
```

```scala
def listAnalysis(list: List[Any]) = list match {
   case Nil => "empty"
   case 'a' :: tail => "starting by 'a'" // or case 'a' :: _ => ...
   case (head:Int) :: _ if head > 3 => "starting by an int greater than 3"
   case (head:Int) :: _ => "starting by an int"
   case _ => "whatever"
}
```

### Pairs

```scala
def (a: Int, b: String): String = (a, b) match {
    case (0, "") => "zero and empty string"
    case (_, "") => "non zero and empty string"
    case _ => "something else"

```
