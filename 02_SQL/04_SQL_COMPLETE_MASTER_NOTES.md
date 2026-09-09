# SQL / RDBMS Complete Master Notes

## Curriculum coverage
SQL, RDBMS, schema, table structure, data types, DDL/DML/DQL/DCL/TCL, queries, keys, referential integrity, normalization, multiplicity/consistency, CREATE/DROP/TRUNCATE, auto-increment, CHECK/DEFAULT/CASCADE, aggregate/scalar functions, clauses, subqueries, joins, aliases, transactions, ACID/CID concepts, CRUD, commit/rollback/isolation, sequences, indexes, triggers, views, procedures, UDFs, schema design.

## 1. Logical query flow
A useful mental model is:
`FROM/JOIN → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY → LIMIT`.
This is conceptual processing order, not a promise about physical execution.

## 2. Core querying
```sql
SELECT employee_id, name, salary
FROM employees
WHERE salary > 50000
ORDER BY salary DESC;
```
Know aliases, `DISTINCT`, `CASE`, `NULL`, dates and string functions.

## 3. Aggregation
```sql
SELECT department, COUNT(*) AS employees, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 60000;
```
`WHERE` filters rows before aggregation; `HAVING` filters grouped results.

## 4. Joins
- INNER: only matching rows.
- LEFT: all left rows + matching right rows.
- RIGHT: all right rows + matching left rows.
- FULL OUTER: all rows from both sides where supported.
- CROSS: Cartesian product.
- SELF: table joined to itself.
- Equi join: equality condition.
- Theta join: broader comparison such as `<` or `>`.

Interview trap: a filter on the right side in `WHERE` can eliminate NULL-extended rows and effectively turn a LEFT JOIN into an INNER-like result.

## 5. Subquery vs CTE
A subquery is nested SQL. A CTE uses `WITH` to name a subquery and can make complex logic easier to read/reuse within a statement.

## 6. Window functions — P0
Window functions calculate over a related set of rows without collapsing the result to one row per group.

```sql
SELECT employee_id, department, salary,
       DENSE_RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS rnk
FROM employees;
```
Know:
- `ROW_NUMBER`: unique sequence within partition.
- `RANK`: ties share rank; gaps can appear.
- `DENSE_RANK`: ties share rank; no gaps.
- `LAG` / `LEAD`.
- running totals.
- moving averages.

## 7. Most important interview patterns
### Third-highest distinct salary
```sql
SELECT salary
FROM (
  SELECT salary,
         DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
  FROM employees
) x
WHERE rnk = 3;
```

### Latest row per customer
```sql
SELECT *
FROM (
  SELECT e.*, ROW_NUMBER() OVER (
      PARTITION BY customer_id ORDER BY updated_at DESC
  ) AS rn
  FROM customer_events e
) x
WHERE rn = 1;
```

### Duplicates
```sql
SELECT business_key, COUNT(*)
FROM t
GROUP BY business_key
HAVING COUNT(*) > 1;
```

### Employee earns more than manager
```sql
SELECT e.employee_id, e.name, e.salary, m.name AS manager_name, m.salary AS manager_salary
FROM employees e
JOIN employees m ON e.manager_id = m.employee_id
WHERE e.salary > m.salary;
```

## 8. Keys and constraints
Primary key = row identity. Composite key = multiple columns together form identity. Foreign key = relationship to another key. Unique = uniqueness constraint. Alternate/secondary key = candidate identifier not chosen as the primary key.

Constraints: `NOT NULL`, `CHECK`, `DEFAULT`, `UNIQUE`, `PRIMARY KEY`, `FOREIGN KEY`.

## 9. Normalization
1NF: atomic values/no repeating groups.
2NF: 1NF + no partial dependency on part of a composite key.
3NF: 2NF + no transitive dependency of non-key attributes on the key.
Denormalization intentionally duplicates/combines data for performance or simpler reads when justified.

## 10. Transactions
ACID:
- Atomicity — all or nothing.
- Consistency — valid state transitions.
- Isolation — concurrent transactions behave according to the selected isolation semantics.
- Durability — committed changes persist.

Know `COMMIT`, `ROLLBACK`, savepoints and isolation levels at a conceptual level. Do not state vendor-specific transaction behavior as universal.

## 11. DELETE / TRUNCATE / DROP
`DELETE` removes rows and can use `WHERE`; `TRUNCATE` removes all rows while retaining the table object; `DROP` removes the object. Recovery/logging/transaction details are database-specific.

## 12. Indexes
Indexes can accelerate selective lookup and joins but add storage and write/maintenance overhead. Indexing strategy depends on workload and database engine.

## 13. Views / procedures / UDFs / triggers
- View: stored query definition.
- Materialized view: maintained computed result where supported.
- Stored procedure: reusable procedural logic.
- UDF: reusable function returning a value/table depending on platform.
- Trigger: logic fired by data/object events where supported.

## 14. SQL optimization
Inspect execution plan/profile, filter early, return needed columns, avoid accidental Cartesian joins, ensure join predicates are correct, aggregate at the correct grain, and use indexes/partitioning/clustering according to the platform.

## Persistent focus
Historical Persistent interview reports repeatedly emphasize SQL coding, window functions, joins, duplicates, latest-row patterns, salary problems and query optimization. Treat exact questions as evidence only when linked to a candidate report; broader patterns are high-probability preparation.
