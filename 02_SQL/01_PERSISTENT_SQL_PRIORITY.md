# SQL — Persistent Interview Priority

## Why SQL is P0
SQL appears repeatedly in current Persistent Data Engineer interview reports, and the fresher Revature pathway explicitly reports coding + SQL + training/resume focus.

## Highest-priority reported patterns
- Employee salary greater than direct manager.
- Third-highest salary with window functions.
- Duplicate detection.
- Latest record per business key using ROW_NUMBER.
- RANK vs DENSE_RANK.
- Department min/max/average.
- Moving average.
- Flight delay aggregation.
- Slow SQL optimization.

## Mastery order
1. SELECT/WHERE/ORDER BY
2. GROUP BY/HAVING
3. JOINs
4. Subqueries
5. CTEs
6. CASE
7. Window functions
8. Deduplication
9. Latest-record patterns
10. Running totals/moving averages
11. Date analytics
12. Query optimization

## Must-code questions
- 2nd highest salary
- 3rd highest salary
- top 3 per department
- employee > manager
- latest row per customer
- duplicates
- customers without orders
- running total
- moving average
- consecutive-day/weekly condition

## Interview rule
Do not just memorize query syntax. Explain the grain, join condition, filtering order and why the window partition/order are correct.

## Sources
- https://www.linkedin.com/posts/anshu-kumar-987381142_dataengineer-snowflake-sql-activity-7448582660375076864-5r36
- https://www.linkedin.com/posts/samrat-ashok-ak_dataengineering-interviewexperience-sql-activity-7405874595129372672-nCxM
- https://www.linkedin.com/posts/bigdatabysumit_applied-for-senior-data-engineer-walked-activity-7451974278096306176-nz4e
