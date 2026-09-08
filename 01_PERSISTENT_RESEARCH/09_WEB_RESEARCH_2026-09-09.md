# Persistent Systems Data Engineer — Web Research Update

**Research date:** 2026-09-09
**Target:** Revature → Persistent Snowflake_MSFabric fresher/client interview

## Evidence reviewed

Recent Persistent-specific material continues to show a practical Data Engineer interview pattern rather than definition-only questioning.

### 1. Recent hands-on Persistent report

A recent Persistent Data Engineer report describes an end-to-end discussion followed by hands-on Python, SQL, Snowflake and PySpark.

Reported areas:
- Project/data-pipeline architecture: Source → Azure → Synapse/PySpark → Snowflake
- Python duplicate removal and second-highest number
- SQL duplicate detection
- `RANK` vs `DENSE_RANK`
- latest-record filtering with `ROW_NUMBER`
- Snowflake external-stage access
- file formats
- `COPY`
- `MERGE`
- `QUALIFY` for deduplication
- Streams / CDC
- PySpark null checks
- `groupBy`
- RDD `map`

Source: Anshu Kumar, Persistent Data Engineer interview experience.

### 2. Repeated Persistent SQL/Spark pattern

Another reported Persistent interview contains:
- employee salary greater than direct manager
- nested JSON parsing/flattening in PySpark
- Azure ADF + Databricks + ADLS pipeline design
- dimensional modeling and sales fact design
- narrow vs wide transformations
- schema evolution
- SCD Type 2 in Spark
- Spark optimization at terabyte scale
- Bronze/Silver/Gold

### 3. Recent Azure/PySpark pattern

A recent Persistent report also describes:
- PySpark data skew and salting
- Python duplicate removal
- Azure Integration Runtime vs Self-Hosted IR
- queued ADF pipeline troubleshooting
- secure secret management
- Star vs Snowflake schema

## What this means for YOUR preparation

### P0 — must be hands-on
1. SQL window functions
2. SQL deduplication
3. SQL joins/self joins
4. Python basic coding
5. PySpark DataFrame operations
6. Snowflake stages and file formats
7. Snowflake COPY
8. Snowflake MERGE
9. Snowflake QUALIFY
10. Snowflake Streams/CDC
11. Spark narrow/wide transformations
12. schema evolution
13. SCD Type 2
14. Spark optimization
15. dimensional modeling
16. ETL/ELT
17. project architecture

### P0 for the Snowflake_MSFabric track
18. Snowflake micro-partitions
19. pruning
20. clustering
21. warehouse sizing/cost
22. Time Travel / Fail-safe
23. zero-copy cloning
24. Snowpark
25. RBAC/masking/RLS
26. Fabric OneLake
27. Lakehouse vs Warehouse
28. Delta + Medallion
29. Fabric Data Factory
30. Fabric SQL endpoint/T-SQL
31. Power BI integration
32. Fabric governance/CI-CD

## Evidence caution

The strongest public reports are not all fresher reports. Some are from 3–5+ years of experience or senior roles. They are useful for topic selection, but they should not be treated as a guarantee of interview depth for a Revature-trained fresher.

For your pathway, the safest assumption is that the interviewer can test the training curriculum, resume/projects, coding, SQL and applied data-engineering reasoning.

## Sources

- Persistent Data Engineer hands-on report: https://www.linkedin.com/posts/anshu-kumar-987381142_dataengineer-snowflake-sql-activity-7448582660375076864-5r36
- Persistent Data Engineer interview report: https://www.linkedin.com/posts/samrat-ashok-ak_dataengineering-interviewexperience-sql-activity-7405874595129372672-nCxM
- Persistent Data Engineer interview report: https://www.linkedin.com/posts/rakesh-dl_dataengineering-dataengineer-interviewpreparation-activity-7475912941670793217-cyaY
- Persistent Data Engineer interview guide: https://dataford.io/interview-guides/persistent-systems/data-engineer
