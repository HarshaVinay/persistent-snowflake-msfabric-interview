# Advanced Database Master Notes

## Transactions
A transaction groups logical operations into a unit of work. Know ACID, commit, rollback and savepoints.

### Isolation levels
Know the anomalies conceptually:
- Dirty read
- Non-repeatable read
- Phantom read
Then understand that implementations and exact guarantees vary by RDBMS.

## CRUD
Create, Read, Update, Delete are the core application data operations. In SQL they commonly map to `INSERT`, `SELECT`, `UPDATE`, `DELETE`.

## Sequences / auto-increment
Used to generate identifiers. Exact syntax and behavior are vendor-specific; the interview goal is understanding surrogate-key generation.

## Indexes
An index is an auxiliary structure used to accelerate access paths. Trade-off: faster reads versus additional storage and maintenance during writes.

## Views
A view stores a query definition. It can simplify consumption, encapsulate joins/filters and present a stable interface.

## Stored procedures
Procedural database-side logic. Use when business logic or operational workflows are appropriate for the database engine.

## UDFs
Reusable functions for custom calculations. Prefer built-in functions when the platform can optimize them better.

## Triggers
Automatic database actions fired by defined events. Useful for specific auditing or integrity workflows, but can hide side effects and complicate debugging if overused.

## Referential actions
`CASCADE`, `RESTRICT`, `SET NULL` or platform-specific behavior define what can happen to child rows when a parent is updated/deleted.

## Schema-design interview checklist
- Identify entities.
- Define grain.
- Choose natural vs surrogate keys.
- Normalize operational data where appropriate.
- Define foreign keys and constraints.
- Decide where denormalization helps analytical workloads.
- Document cardinality/multiplicity.
- Validate nullability and uniqueness.

## Interview question
**Why not put everything in one table?**
“Because it creates duplication, update anomalies, wider rows and harder maintenance. I would normalize operational data to maintain integrity, then use dimensional/denormalized structures for analytical workloads when justified.”
