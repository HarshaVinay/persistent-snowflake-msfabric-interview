# SQL Joins, Subqueries and CTEs

## Join mental model
A join combines rows from relations using a matching condition.

### INNER JOIN
Returns matched rows from both sides.
```sql
SELECT e.employee_id, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id;
```

### LEFT JOIN
Keeps every left row and matches the right where possible.

### RIGHT JOIN
Keeps every right row. Know it conceptually; many teams prefer rewriting it as a LEFT JOIN for readability.

### FULL OUTER JOIN
Keeps matched and unmatched rows from both sides where the engine supports it.

### CROSS JOIN
Cartesian product. Use deliberately; row counts can multiply dramatically.

### SELF JOIN
A table joined to itself, e.g. employee → manager.

### Equi join
Join predicate uses equality.

### Theta join
Join predicate can use conditions such as <, >, <= or !=.

## Join interview traps
1. Know the grain of both tables before joining.
2. A one-to-many join can multiply rows.
3. Check duplicates on the join key.
4. Put right-table filters deliberately: ON vs WHERE changes LEFT JOIN semantics.
5. Avoid CROSS JOIN unless required.

## Subquery
A query nested inside another query.

Common forms:
- scalar subquery
- correlated subquery
- subquery in WHERE
- subquery in FROM
- subquery in SELECT

Example:
```sql
SELECT employee_id, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

## CTE
A Common Table Expression names a query block with `WITH`.

```sql
WITH dept_avg AS (
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY department_id
)
SELECT *
FROM dept_avg;
```

### CTE vs subquery
Both structure nested logic. CTEs usually improve readability and can be referenced multiple times within the statement, but materialization behavior is database-specific.

## Interview follow-ups
- When would a join be safer than a subquery?
- What happens when a subquery returns multiple rows where one row is expected?
- Why can an unplanned join duplicate records?
- Can a CTE improve performance? Answer carefully: primarily readability/reuse; optimization/materialization is engine-specific.
