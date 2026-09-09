# Python Core Interview Notes

## Execution model
Python is generally executed by an interpreter/runtime rather than being compiled ahead of time in the same model as a typical C/C++ workflow. CPython compiles source to bytecode internally before execution.

## Core types
`int`, `float`, `complex`, `bool`, `str`, `list`, `tuple`, `set`, `dict`, `bytes`, `bytearray`, `NoneType`.

## Mutable vs immutable
- Mutable: list, dict, set, bytearray.
- Immutable: int, float, bool, str, tuple, bytes.

Why it matters: mutating a shared mutable object can change state seen by another reference.

## List vs tuple vs set
| Type | Ordered | Mutable | Duplicate values |
|---|---|---|---|
| list | Yes | Yes | Yes |
| tuple | Yes | No | Yes |
| set | No guaranteed positional order | Yes | No |

## Dictionary
Maps keys to values. Keys must satisfy hashability requirements.

## `==` vs `is`
- `==` compares value equality.
- `is` compares object identity.

## Functions
Know positional/keyword arguments, defaults, `*args`, `**kwargs`, lambda functions and return values.

## Scope
Remember LEGB:
**Local → Enclosing → Global → Built-in.**

## Comprehensions
```python
squares = [x * x for x in range(10)]
```
Use for concise transformations, but prefer readable loops when logic becomes complex.

## Iterator vs generator
An iterator supplies values through the iterator protocol. A generator is a convenient way to create lazy iterators, typically with `yield`.

## Exception handling
```python
try:
    value = int(text)
except ValueError:
    value = 0
finally:
    cleanup()
```
Catch specific exceptions. Avoid broad `except Exception` unless you have a deliberate recovery/logging reason.

## File handling
Prefer context managers:
```python
with open("data.json", "r", encoding="utf-8") as f:
    data = f.read()
```

## JSON
```python
import json
obj = json.loads(text)
text = json.dumps(obj)
```

## Regex
Use `re` for pattern matching/extraction. Avoid regex when a simpler string method is clearer.

## OOP
Four core ideas:
- Encapsulation
- Abstraction
- Inheritance
- Polymorphism

## Logging
Prefer structured logging over scattered `print()` statements in production-style code.

## Interview coding habits
State inputs, outputs, assumptions and edge cases before coding. Test empty input, duplicate values, null-like values and boundary cases.
