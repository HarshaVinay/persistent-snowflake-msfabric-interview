# Persistent SQL Master — Snowflake_MSFabric Track

## Priority
**P0 — must be interview-ready.**

Recent Persistent reports repeatedly emphasize SQL coding, especially window functions, joins, duplicate handling, latest-record logic and query optimization.

## Reported question patterns

### 1. Employees earning more than their manager
Core pattern: self-join employee table to itself using manager_id.

### 2. Third-highest salary
Use a window function such as DENSE_RANK when distinct salary ranking is intended.

### 3. Duplicate records
GROUP BY business key + HAVING COUNT(*) > 1, or ROW_NUMBER for identifying/removing duplicate rows.

### 4. Latest record per business key
ROW_NUMBER() OVER (PARTITION BY business_key ORDER BY updated_at DESC), then filter rn = 1. In Snowflake, QUALIFY is a clean alternative.

### 5. RANK vs DENSE_RANK
RANK leaves gaps after ties; DENSE_RANK does not. ROW_NUMBER assigns a unique sequence within the window.

## Additional P0 SQL
- INNER/LEFT/RIGHT/FULL joins
- self joins
- CTEs
- subqueries
- GROUP BY/HAVING
- CASE expressions
- NULL handling
- LEAD/LAG
- running totals
- moving averages
- top N per group
- conditional aggregation
- query optimization

## Snowflake-specific SQL
Know QUALIFY, MERGE, COPY INTO, stages, file formats and semi-structured querying.

## Interview rule
Do not just produce the query. Explain:
1. grain of the data;
2. why the join is safe;
3. whether ties matter;
4. how NULLs behave;
5. performance considerations.

## Sources
- https://www.linkedin.com/posts/anshu-kumar-987381142_dataengineer-snowflake-sql-activity-7448582660375076864-5r36
- https://www.linkedin.com/posts/samrat-ashok-ak_dataengineering-interviewexperience-sql-activity-7405874595129372672-nCxM
- https://www.linkedin.com/posts/nupur-zavery-4a47811b0_persistent-systems-offered-my-one-friend-activity-7415751576037822464-cnpt
- https://dataford.io/interview-guides/persistent-systems/data-engineer

## Status
Reported patterns are evidence. Any additional question not explicitly reported is a preparation prediction.