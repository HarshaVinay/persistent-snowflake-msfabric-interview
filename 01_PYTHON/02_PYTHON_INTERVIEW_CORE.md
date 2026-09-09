# Python Interview Core — Persistent Snowflake_MSFabric

## Scope
Interpreter/compiler, REPL/Jupyter, Python fundamentals, data structures, functions, scope, iterators/generators, OOP, exceptions, files, JSON, regex, modules/packages, logging and data-engineering coding patterns.

## Execution model
Python is interpreted through a runtime; CPython compiles source to bytecode internally before execution. For an interview, distinguish source code, bytecode and runtime execution rather than saying simply that Python is “not compiled.”

## Core types
`int`, `float`, `complex`, `bool`, `str`, `list`, `tuple`, `set`, `dict`, `bytes`, `bytearray`, `NoneType`.

## Mutability
Mutable: list, dict, set, bytearray.
Immutable: int, float, bool, str, tuple, bytes.

Why it matters: mutating a shared mutable object changes the object observed through other references.

## List vs tuple vs set
| Type | Ordered | Mutable | Duplicates |
|---|---|---|---|
| list | Yes | Yes | Yes |
| tuple | Yes | No | Yes |
| set | No positional order guarantee | Yes | No |

## Dictionary
A key/value mapping. Keys must satisfy hashability requirements.

## `==` vs `is`
- `==` checks value equality.
- `is` checks object identity.

## Functions
Know positional/keyword arguments, defaults, `*args`, `**kwargs`, lambda, comprehensions, higher-order functions, return values and recursion basics.

## Scope
Use LEGB: Local → Enclosing → Global → Built-in.

## Iterators and generators
An iterator follows the iterator protocol. A generator is a convenient lazy iterator, usually created with `yield`.

## OOP
Know encapsulation, abstraction, inheritance and polymorphism; classes vs objects; instance/class attributes; constructors; overriding; `super()`.

## Exceptions
Catch specific exceptions and keep recovery logic explicit. Know `try`, `except`, `else`, `finally`; avoid bare `except` unless deliberately justified.

```python
try:
    value = int(text)
except ValueError:
    value = 0
finally:
    cleanup()
```

## Files and JSON
Prefer context managers:

```python
with open("data.json", "r", encoding="utf-8") as f:
    data = f.read()
```

```python
import json
obj = json.loads(text)
text = json.dumps(obj)
```

Know `load/loads` and `dump/dumps`.

## Regex
Know the `re` module, pattern matching and extraction. Prefer simpler string operations when they are clearer.

## Logging
Use logging for operational visibility rather than relying on `print()` in production-style code.

## Data-engineering coding patterns
- frequency counting with `Counter`
- remove duplicates while preserving order
- find second-largest value
- group records by key
- find latest record by timestamp
- parse/transform JSON
- validate rows
- read and write files

## Interview habits
State assumptions, input/output, edge cases and complexity before or while coding. Test empty input, duplicates, null-like values and boundary cases.

## High-value questions
1. List vs tuple vs set?
2. Mutable vs immutable?
3. `==` vs `is`?
4. Iterator vs generator?
5. `*args` vs `**kwargs`?
6. Explain LEGB.
7. Explain the four OOP principles.
8. `try/except/else/finally`?
9. `json.load` vs `json.loads`?
10. Why use a context manager for files?
