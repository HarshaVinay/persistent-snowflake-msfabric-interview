# Scala Complete Master Notes

## Curriculum scope
Setup, functional programming, variables/values, types, conditions, loops, classes/objects, class structure, expressions/statements, tuples, pure/impure functions, higher-order functions, exceptions, List/Map/Set, review.

## val vs var
`val` is immutable/reassignment is not allowed; `var` can be reassigned. Prefer `val` when possible.

## Expression vs statement
Scala emphasizes expressions: many constructs return values.

## Functions
```scala
def add(a: Int, b: Int): Int = a + b
val square = (x: Int) => x * x
```

## Functional programming
Pure function: same input → same output and no observable side effects. Impure function may depend on/change external state.

Higher-order function accepts or returns functions.

```scala
val nums = List(1,2,3,4)
val result = nums.filter(_ % 2 == 0).map(_ * 10)
```

## Collections
- List: ordered, immutable by default.
- Set: unique elements.
- Map: key-value pairs.
Know `map`, `filter`, `flatMap`, `reduce`, `foreach`.

## Classes / objects
A class is an object blueprint. A Scala `object` defines a singleton object.

## Case classes
Useful for data modeling and pattern matching. They provide generated methods such as equality/copy and companion-object helpers.

## Pattern matching
```scala
value match {
  case 1 => "one"
  case _ => "other"
}
```
Know guards and case-class extraction.

## UDF in Spark
A Scala UDF provides custom row-level logic when built-in Spark functions cannot conveniently express the requirement. Prefer built-in Spark functions when possible because Spark can optimize native expressions more effectively.

## Exceptions
Use `try/catch/finally`; Scala also commonly models recoverable errors using `Option`/`Either` depending on design.

## Persistent interview focus
Know Scala primarily as the language behind many Spark APIs. Be comfortable reading simple collection transformations and explaining functional concepts; do not spend more preparation time here than on SQL/Spark/Snowflake/Fabric.
