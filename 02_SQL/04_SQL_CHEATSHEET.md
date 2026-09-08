# SQL Cheatsheet

## Order of logical processing
FROM/JOIN → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY → LIMIT/OFFSET (engine-specific).

## Joins
INNER = matching rows. LEFT = all left + matches. RIGHT = all right + matches. FULL = all rows from both sides where supported. CROSS = Cartesian product. SELF = table joined to itself.

## Window
`ROW_NUMBER()` unique sequence; `RANK()` ties share rank and gaps can appear; `DENSE_RANK()` ties share rank without gaps.

## Common snippets
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

```sql
WITH ranked AS (
  SELECT e.*, DENSE_RANK() OVER (ORDER BY salary DESC) rnk
  FROM employees e
)
SELECT * FROM ranked WHERE rnk = 3;
```

```sql
SELECT e.*, m.name AS manager_name
FROM employees e
JOIN employees m ON e.manager_id = m.employee_id;
```

## Optimization checklist
Avoid `SELECT *`; filter early; inspect execution plan; verify indexes/partitioning where applicable; reduce unnecessary joins; avoid functions on indexed/filter columns when they defeat access paths; check cardinality and duplicate-causing joins; validate with realistic data.
