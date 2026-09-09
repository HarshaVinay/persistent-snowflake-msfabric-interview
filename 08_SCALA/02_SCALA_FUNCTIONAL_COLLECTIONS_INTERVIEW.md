# Scala Functional Programming & Collections

## Core syntax
```scala
val fixed = 10
var changing = 20
```
Prefer `val` unless reassignment is needed.

## Expression vs statement
Scala is expression-oriented: many constructs produce values.

## Functions
```scala
def add(a: Int, b: Int): Int = a + b
val square = (x: Int) => x * x
```

## Higher-order functions
Functions can take functions as parameters or return functions.

## Pure vs impure
- Pure: same input → same output, no externally visible side effects.
- Impure: can modify external state or depend on side effects.

## Collections
### List
Ordered immutable sequence by default.

### Set
Collection designed around unique elements.

### Map
Key-value mapping.

Common operations:
```scala
numbers.map(_ * 2)
numbers.filter(_ > 10)
numbers.reduce(_ + _)
```

## Case class
Useful for data modeling. Pattern matching works naturally with case classes.

## Pattern matching
```scala
value match {
  case 1 => "one"
  case _ => "other"
}
```

## Spark connection
Scala is one of Spark's native implementation languages. Built-in Spark functions are generally preferred to arbitrary UDFs because Spark can reason about native expressions more effectively.

## Interview questions
- `val` vs `var`?
- List vs Set vs Map?
- map vs filter vs reduce?
- What is a higher-order function?
- Pure vs impure function?
- Class vs case class?
- Why prefer built-in Spark functions over UDFs?
