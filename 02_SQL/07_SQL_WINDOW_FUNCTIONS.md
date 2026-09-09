# SQL Window Functions

## Core idea
A window function calculates across related rows while keeping the individual rows visible.

Syntax:
```sql
function(...) OVER (
  PARTITION BY ...
  ORDER BY ...
  ROWS/RANGE ...
)
```

## ROW_NUMBER
Assigns a unique sequence within each window.
```sql
SELECT *, ROW_NUMBER() OVER (
  PARTITION BY department_id ORDER BY salary DESC
) AS rn
FROM employees;
```

## RANK
Ties share a rank and later positions can have gaps.

## DENSE_RANK
Ties share a rank but there are no gaps.

### Classic interview problem
Third-highest salary:
```sql
SELECT salary
FROM (
    SELECT salary,
           DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
    FROM employees
) x
WHERE rnk = 3;
```
Use DISTINCT/appropriate grain when the requirement is “third-highest distinct salary.”

## Latest record per customer
```sql
SELECT *
FROM (
    SELECT t.*,
           ROW_NUMBER() OVER (
               PARTITION BY customer_id
               ORDER BY updated_at DESC
           ) AS rn
    FROM customer_history t
) x
WHERE rn = 1;
```

## Running total
```sql
SUM(amount) OVER (
    PARTITION BY customer_id
    ORDER BY order_date
    ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
)
```

## Moving average
```sql
AVG(amount) OVER (
    ORDER BY order_date
    ROWS BETWEEN 2 PRECEDING AND CURRENT ROW
)
```

## LEAD / LAG
- `LAG` looks backward.
- `LEAD` looks forward.

Useful for comparing current vs previous/next event.

## FIRST_VALUE / LAST_VALUE
Useful for comparing a row with the first/last row in its window. Be careful with the window frame for LAST_VALUE because default frames differ by database.

## QUALIFY
Some platforms, notably Snowflake, support `QUALIFY` to filter results of window functions without wrapping them in another query:
```sql
SELECT *, ROW_NUMBER() OVER (
  PARTITION BY customer_id ORDER BY updated_at DESC
) rn
FROM customer_history
QUALIFY rn = 1;
```

## Interview traps
- Window functions do not collapse rows like GROUP BY.
- PARTITION BY is not the same as table partitioning.
- RANK and DENSE_RANK differ only after ties, but that difference matters in ranking questions.
- ROW_NUMBER is appropriate when exactly one row must survive per group.
