# SQL / RDBMS Master Notes — Persistent Snowflake_MSFabric

## Curriculum coverage
SQL/RDBMS, schemas, tables, data types, DDL/DML/DQL/DCL/TCL, queries, primary/composite/foreign/unique/alternate keys, referential integrity, normalization, multiplicity, consistency, CREATE/DROP/TRUNCATE, auto-increment, CHECK/DEFAULT/CASCADE, aggregate/scalar functions, clauses, subqueries, joins, aliases, transactions, ACID, CRUD, commit/rollback/isolation, sequences, indexes, triggers, views, stored procedures, UDFs, schema design, constraints, joins/subqueries review.

## SQL mental model
```text
SELECT
FROM
JOIN
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
```
Conceptually understand logical query processing rather than memorizing syntax order alone.

## Keys
Primary key uniquely identifies a row. Composite key uses multiple columns. Foreign key references a parent key. Unique key enforces uniqueness. Alternate/secondary key can identify a candidate unique attribute not chosen as primary key.

## DDL/DML/DQL/DCL/TCL
DDL: CREATE, ALTER, DROP, TRUNCATE.
DML: INSERT, UPDATE, DELETE.
DQL: SELECT.
DCL: GRANT, REVOKE.
TCL: COMMIT, ROLLBACK, SAVEPOINT.

## Joins
INNER, LEFT, RIGHT, FULL OUTER, CROSS, SELF, EQUI and THETA joins. Always state expected row grain before choosing the join.

## Aggregation
`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`; combine with GROUP BY and HAVING.

## Window functions — P0
```sql
SELECT employee_id, department, salary,
       ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC) AS rn,
       RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS rnk,
       DENSE_RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS drnk
FROM employees;
```
ROW_NUMBER gives unique sequence; RANK leaves gaps after ties; DENSE_RANK does not.

## Top N per group
Use a window function partitioned by the group and filter on the assigned rank/row number.

## Latest record
```sql
SELECT *
FROM (
  SELECT t.*, ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY updated_at DESC) rn
  FROM customer_changes t
) x
WHERE rn = 1;
```
Snowflake can simplify the pattern with `QUALIFY`.

## CTE vs subquery
CTE (`WITH`) improves readability/composability and can be referenced by name within a statement. A subquery nests directly inside another query expression.

## WHERE vs HAVING
WHERE filters rows before grouping; HAVING filters groups after aggregation.

## NULL
`NULL` means missing/unknown, not zero or empty string. Use `IS NULL`/`IS NOT NULL`; use `COALESCE` when a business default is justified.

## Transactions / ACID
Atomicity, Consistency, Isolation and Durability describe transaction guarantees in transactional systems. Exact isolation levels and transaction semantics vary by database.

## Indexes
Indexes can speed selective access but add storage/write-maintenance cost. Snowflake's architecture differs from traditional OLTP indexing; do not blindly transfer MySQL index advice to Snowflake.

## Views/procedures/UDFs
View = stored query definition. Stored procedure = procedural workflow/business logic. UDF = reusable custom expression/function.

## Persistent high-value questions
- second/third highest salary.
- employee salary > manager.
- duplicate/latest row.
- joins/window functions.
- moving average.
- query optimization.
- SQL + Snowflake `QUALIFY`/`MERGE` patterns.

## Coding checklist
[ ] top N per group
[ ] duplicate detection/removal
[ ] latest record
[ ] running total
[ ] moving average
[ ] employee-manager self join
[ ] customers without orders
[ ] conditional aggregation
[ ] date grouping
[ ] NULL-safe joins
