# Python Master Notes — Persistent Snowflake_MSFabric

## Curriculum coverage
Interpreter/compiler, REPL/Jupyter, syntax, comments, variables/types, operators, I/O, namespaces, strings, sets, casting, boolean, lists, tuples, range, binary, None, dictionaries, numbers, datetime, conditions, loops, functions, arrays, lambda, classes/objects, OOP, iterators, scope, modules, logging, JSON, regex, pip, pylint, errors, exceptions, try/except, files.

## Core mental model
Python is dynamically typed and strongly typed. Names refer to objects; variables are bindings, not fixed typed boxes.

## Must-know data structures
- list: ordered, mutable.
- tuple: ordered, immutable.
- set: unique elements, unordered.
- dict: key/value mapping.
- string: immutable sequence of characters.

## Interview contrasts
- `==` compares values; `is` tests object identity.
- Mutable: list, dict, set. Immutable: int, float, bool, str, tuple, frozenset.
- Iterator supplies values one at a time and maintains iteration state.
- Generator is a convenient lazy iterator, commonly using `yield`.
- `range()` produces a lazy range object in Python 3.

## Functions
Know positional/keyword arguments, defaults, `*args`, `**kwargs`, lambda, comprehensions, higher-order functions, recursion basics, scope (LEGB).

## OOP
Encapsulation, inheritance, polymorphism, abstraction; instance vs class attributes; constructors; method overriding; `super()`.

## Exceptions
Prefer targeted exception handling. Use `finally` for cleanup when needed. Avoid bare `except` unless justified.

## JSON/files
Know `json.load`, `json.loads`, `json.dump`, `json.dumps`; context manager `with open(...)`.

## Data-engineering emphasis
Be able to write small scripts for CSV/JSON ingestion, validation, deduplication, transformation and file output. Logging should capture useful operational context rather than replacing error handling.

## Coding patterns
- frequency counter
- remove duplicates while preserving order
- latest record by timestamp
- group records by key
- parse JSON
- validate fields
- transform a list of dictionaries

## Interview answer
"I use Python as the orchestration and transformation language around data pipelines. For larger distributed processing I move the heavy transformations to PySpark rather than forcing large datasets through single-machine Python objects."

## Priority
P0 for coding; P1 for language internals.
