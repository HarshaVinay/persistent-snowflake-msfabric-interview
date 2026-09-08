# SQL — Persistent Reported Patterns 2026

## Why this file exists

This is not a generic SQL tutorial. It maps **reported Persistent interview questions** to the SQL topics in your Snowflake_MSFabric curriculum.

## P0 — reported repeatedly

### 1. Employee earning more than direct manager

**Pattern:** self join.

```sql
SELECT e.employee_id,
       e.employee_name,
       e.salary,
       m.employee_name AS manager_name,
       m.salary AS manager_salary
FROM employees e
JOIN employees m
  ON e.manager_id = m.employee_id
WHERE e.salary > m.salary;
```

**What interviewer is testing:** joins, aliases, relational reasoning.

Reported in Persistent interview experiences. citeturn1search2turn1search8

---

### 2. Duplicate records

```sql
SELECT business_key, COUNT(*)
FROM target_table
GROUP BY business_key
HAVING COUNT(*) > 1;
```

For deletion, use a window function and keep exactly one record according to an explicit business rule.

Persistent reports explicitly include duplicate detection/removal. citeturn1search0turn1search12

---

### 3. RANK vs DENSE_RANK vs ROW_NUMBER

Know the behavior with ties, not just definitions.

- `ROW_NUMBER()` gives every row a unique sequence.
- `RANK()` gives equal values the same rank and leaves gaps after ties.
- `DENSE_RANK()` gives equal values the same rank without gaps.

Persistent reports explicitly mention this comparison. citeturn1search12

---

### 4. Latest record per business key

```sql
SELECT *
FROM source_table
QUALIFY ROW_NUMBER() OVER (
    PARTITION BY id
    ORDER BY updated_date DESC
) = 1;
```

The generic window-function form is widely useful; `QUALIFY` is particularly relevant because a recent Persistent Snowflake interview report explicitly used it for deduplication. citeturn1search12

---

### 5. Second/third highest salary

Be ready to solve using:
- subquery
- CTE
- `DENSE_RANK`
- `ROW_NUMBER` where appropriate

Persistent reports explicitly mention second/third-highest salary and window functions. citeturn0search3turn0search2

---

### 6. More than 20 critical orders every week for at least one month

This is a higher-level SQL analytics problem.

Expected reasoning:
1. filter critical orders;
2. derive the week;
3. count per user/week;
4. keep weeks above threshold;
5. count qualifying weeks per user;
6. apply the one-month requirement.

This exact pattern is reported in Persistent interview experiences. citeturn1search2turn1search8

---

## P0 concepts from the curriculum

You must be able to explain and code:

- DDL/DML/DQL/DCL/TCL
- keys and constraints
- normalization
- aggregate/scalar functions
- clauses
- aliases
- joins
- subqueries
- transactions
- commit/rollback
- isolation levels
- indexes
- views
- stored procedures
- UDFs
- schema design
- window functions

## P0 interview drills

1. Top 3 salaries per department.
2. Latest order per customer.
3. Customers with no orders.
4. Running revenue by day.
5. Seven-day moving average.
6. Duplicate customers with different update timestamps.
7. Employee-manager salary comparison.
8. Users crossing a weekly threshold for four weeks.
9. Deduplicate while retaining the latest record.
10. Explain why a LEFT JOIN can accidentally become an INNER JOIN.

## SQL optimization checklist

When asked to optimize a query, do not immediately say “add an index.”

First discuss:

1. execution plan;
2. row counts/cardinality;
3. filters and predicate selectivity;
4. unnecessary columns;
5. join strategy;
6. aggregation placement;
7. repeated scans;
8. partitioning/clustering where the platform supports it;
9. statistics;
10. workload/concurrency considerations.

Persistent interview reports explicitly include slow-query optimization. citeturn1search0

## Source note

These questions are evidence-backed. The exact database engine can differ by candidate/project, so practice syntax in both conventional SQL and Snowflake SQL where relevant.
