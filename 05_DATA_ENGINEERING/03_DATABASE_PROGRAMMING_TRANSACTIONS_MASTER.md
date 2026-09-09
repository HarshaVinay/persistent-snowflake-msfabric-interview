# Database Programming & Transactions Master Notes

## Curriculum coverage
CRUD, CID/ACID properties, transactions, commit/rollback, isolation levels, sequences, indexes, triggers, views, stored procedures, UDFs, schema design and constraints.

## CRUD
Create = INSERT; Read = SELECT; Update = UPDATE; Delete = DELETE.

## ACID
Atomicity = all-or-nothing.
Consistency = valid state according to rules/constraints.
Isolation = concurrent transactions are controlled according to isolation level.
Durability = committed changes persist.

## COMMIT / ROLLBACK
`COMMIT` makes a transaction's changes durable according to the database semantics. `ROLLBACK` undoes uncommitted work within the applicable transaction scope.

## Isolation levels
Know the ideas behind dirty reads, non-repeatable reads and phantom reads. Exact supported levels and behavior vary by DBMS.

## Indexes
Improve lookup paths for selective access at the cost of extra storage and maintenance. Traditional indexes are an OLTP concept; Snowflake uses a different architecture and automatic micro-partition metadata.

## Sequences / auto-increment
Generate surrogate identifiers. Know the difference between a generated numeric key and a business key.

## Views
Reusable query abstraction. Good for simplifying access and encapsulating logic.

## Stored procedures
Procedural database-side logic/workflows.

## UDFs
Reusable function logic for expressions. Avoid creating UDFs when built-in functions solve the problem more efficiently.

## Triggers
Database-triggered actions on events. Useful but can hide behavior and complicate maintenance; explain trade-offs.

## Schema design
Start from business entities and relationships, define keys/grain/constraints, normalize operational models, then denormalize or dimensionalize for analytics where appropriate.

## Interview questions
- Explain ACID.
- What is transaction isolation?
- DELETE vs TRUNCATE vs DROP.
- Index advantages/trade-offs.
- View vs stored procedure vs UDF.
- Why use surrogate keys?
- What is referential integrity?
