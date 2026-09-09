# SQL Core Concepts

## What is SQL?
SQL is the language used to define, query, manipulate and control relational data.

## RDBMS
An RDBMS stores related data in tables and enforces relationships/constraints between tables.

## Schema and table
A schema is a logical namespace for database objects. A table stores rows organized by columns.

## SQL sublanguages
| Type | Purpose | Examples |
|---|---|---|
| DDL | Define/alter structure | CREATE, ALTER, DROP, TRUNCATE |
| DML | Change rows | INSERT, UPDATE, DELETE, MERGE |
| DQL | Read data | SELECT |
| DCL | Permissions | GRANT, REVOKE |
| TCL | Transaction control | COMMIT, ROLLBACK, SAVEPOINT |

## Keys
- Primary key: identifies a row.
- Composite key: key made from multiple columns.
- Foreign key: references a key in another table.
- Unique key: enforces uniqueness according to the DBMS rules.
- Alternate/secondary key: candidate key not selected as the primary key.

## Constraints
NOT NULL, UNIQUE, PRIMARY KEY, FOREIGN KEY, CHECK and DEFAULT are common integrity constraints.

## CREATE / DROP / TRUNCATE / DELETE
- DELETE removes rows and can use WHERE.
- TRUNCATE removes all rows while retaining the table object, with DBMS-specific transaction/logging behavior.
- DROP removes the object.

Do not assume identical transactional behavior across MySQL, Snowflake and Fabric SQL.

## Functions
Aggregate functions reduce multiple rows: COUNT, SUM, AVG, MIN, MAX.
Scalar functions transform individual values: string, date, numeric and conditional functions.

## Aliases
Aliases improve readability:
```sql
SELECT e.employee_id, e.salary
FROM employees e;
```

## Logical query processing
A useful conceptual order is:
FROM/JOIN → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY → LIMIT/FETCH.

This explains why a SELECT alias is often unavailable in WHERE and why HAVING works after grouping.

## NULL
NULL means missing/unknown, not zero and not an empty string.
Use `IS NULL` and `IS NOT NULL`.

## Interview traps
- WHERE filters rows; HAVING filters groups.
- `COUNT(*)` counts rows; `COUNT(column)` ignores NULLs in that column.
- A LEFT JOIN plus a right-side filter in WHERE can unintentionally remove unmatched rows.
- Always state database dialect when behavior is vendor-specific.
