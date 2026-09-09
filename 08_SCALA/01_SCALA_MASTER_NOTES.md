# Scala Master Notes — Persistent Snowflake_MSFabric

## Curriculum coverage
Setup, functional programming, variables/values, data types, conditions, loops, classes/objects, class structure, expression vs statement, tuples, pure/impure functions, higher-order functions, exception handling, List/Map/Set, review.

## Core
`val` is immutable by default; `var` is mutable. Scala is strongly and statically typed with concise syntax and strong functional-programming support.

## Collections
- `List`: ordered immutable sequence commonly used in functional transformations.
- `Map`: key/value association.
- `Set`: unique elements.

## Functional programming
Know pure vs impure functions, immutability, higher-order functions, lambdas, `map`, `filter`, `flatMap`, `reduce`, `foreach`.

```scala
val nums = List(10,20,30,40)
val result = nums.filter(_ > 20).map(_ * 2)
```

## Classes and case classes
A case class is designed for data modeling and supports generated methods such as `apply`, `unapply`, `copy`, equality and `toString`.

## Pattern matching
```scala
value match {
  case 1 => println("one")
  case _ => println("other")
}
```

## Spark connection
Scala is one of Spark's native JVM languages. Interviewers may connect Scala functional operations with Spark transformations.

## UDF rule
Prefer built-in Spark functions over UDFs when possible because the engine can optimize built-ins more effectively; use UDFs for genuinely custom logic.

## Likely interview questions
- `val` vs `var`.
- List vs Set vs Map.
- `map` vs `flatMap`.
- Pure vs impure function.
- Higher-order function.
- Case class vs normal class.
- Pattern matching.
- `apply` vs `unapply`.
- Why prefer built-in Spark functions over UDFs?

## Priority
P1: know the curriculum well enough to explain and write small examples; do not spend disproportionate time on Scala over SQL/PySpark/Snowflake.
