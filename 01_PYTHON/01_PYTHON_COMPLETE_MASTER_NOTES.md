# Python Complete Master Notes

## Scope from curriculum
Interpreter vs compiler, REPL/Jupyter, Python basics, variables/types, operators, I/O, namespaces, strings, sets, casting, boolean, lists, tuples, range, binary, None, dictionaries, numbers, datetime, if/elif/else, loops, functions, arrays, lambda, classes/objects, inheritance, abstraction, polymorphism, encapsulation, iterators, scope, modules, logging, JSON, regex, pip, pylint, errors, exceptions, try/except, files.

## 1. Python mental model
Python is a high-level general-purpose language. In common implementations such as CPython, source is compiled to bytecode and executed by a virtual machine. For interviews, say: **Python is interpreted at runtime, but the implementation performs compilation to bytecode first.** Avoid an absolute “Python is only interpreted” statement.

## 2. Core data types
- `int`, `float`, `complex`
- `bool`
- `str`
- `list`, `tuple`, `set`, `dict`
- `NoneType`
- `bytes`, `bytearray`

### Mutable vs immutable
Mutable: list, dict, set, bytearray.
Immutable: int, float, bool, str, tuple, bytes, frozenset.

## 3. High-value collections
```python
items = [10, 20, 30]
coords = (10, 20)
unique = {10, 20, 30}
row = {"id": 101, "name": "Ravi"}
```

Know membership, iteration, slicing, copying, unpacking, comprehension and complexity at a practical level.

## 4. Functions
```python
def total(a, b=0):
    return a + b
```
Know positional/keyword arguments, defaults, `*args`, `**kwargs`, lambda and scope.

## 5. OOP
Four pillars:
- Encapsulation — bundle data and behavior; restrict direct access when appropriate.
- Abstraction — expose essential behavior while hiding implementation details.
- Inheritance — derive behavior from another class.
- Polymorphism — same interface/operation with different implementations.

## 6. Iterators and generators
An iterator produces values one at a time with `__next__`. A generator uses `yield` and is useful for lazy processing and memory efficiency.

## 7. Exceptions
```python
try:
    value = int(text)
except ValueError as exc:
    logger.exception("Invalid integer")
    raise
```
Know `try/except/else/finally`, specific exceptions, re-raising, custom exceptions and avoiding broad `except Exception` unless deliberate.

## 8. Files and JSON
Prefer context managers:
```python
with open("data.json", "r", encoding="utf-8") as f:
    payload = json.load(f)
```
Know read/write/append, text vs binary, JSON serialize/deserialize.

## 9. Regex
Use regex for pattern validation/extraction, not as a replacement for parsers when structure is complex.

## 10. Logging
Use structured log levels: DEBUG, INFO, WARNING, ERROR, CRITICAL. Never print secrets or credentials.

## 11. Modules, pip, pylint
Know package/module/import basics, virtual environments, dependency installation, linting and reproducible requirements.

## 12. Coding patterns
- Count frequencies with `Counter`.
- Remove duplicates while preserving order with a `set` plus list.
- Find second-largest distinct number.
- Reverse string / palindrome.
- Flatten nested lists.
- Group records by key.
- Sort dictionaries by value.
- Read JSON and normalize records.

## Interview answers
### “Why Python for data engineering?”
“Python has a large data ecosystem, readable syntax, strong file/API/database support, and first-class integration with tools such as Pandas, PySpark and cloud SDKs. For large distributed processing I use PySpark rather than assuming pure Python should process all large data on one machine.”

### “List vs tuple?”
“Both are ordered sequences, but lists are mutable while tuples are immutable. I use lists when the collection changes and tuples for fixed structured values.”

## Project connection
Project 1 uses Python/Pandas for cleaning and ETL. Project 2 uses Python as the orchestration/transformation glue around SQL, Airflow and dbt-related workflows.
