# Snowflake — Persistent Interview Priority

## Current evidence
A recent Persistent Data Engineer interview report directly combines Snowflake with SQL and PySpark. Reported Snowflake tasks include external stages, file formats, COPY, MERGE/upsert, QUALIFY-based deduplication and Streams for CDC/incremental pipelines.

Source: https://www.linkedin.com/posts/anshu-kumar-987381142_dataengineer-snowflake-sql-activity-7448582660375076864-5r36

## P0
1. Architecture
2. Storage vs compute
3. Virtual warehouses
4. Micro-partitions
5. Pruning
6. Clustering
7. Stages
8. File formats
9. COPY INTO
10. MERGE
11. QUALIFY
12. Deduplication
13. Streams / CDC
14. Semi-structured data / VARIANT / FLATTEN
15. Query Profile
16. Caching
17. Warehouse sizing and cost
18. Time Travel
19. Fail-safe
20. Zero-copy cloning
21. RBAC
22. Masking / row access
23. Snowpark

## Why MERGE + Streams are elevated
The latest public interview report specifically reports both. They also connect directly to ETL/ELT, incremental loading and SCD-style workflows in the user's curriculum.

## Do not overclaim
The public report does not prove that every Persistent Snowflake interview asks every Snowflake topic. Topics such as micro-partitions, clustering, Snowpark and security are P0 because they are central to the user's actual specialization, not because they are all confirmed historical questions.
