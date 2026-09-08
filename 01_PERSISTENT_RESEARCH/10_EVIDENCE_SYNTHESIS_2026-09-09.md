# Persistent Interview Evidence Synthesis — 2026-09-09

## Scope
This document synthesizes current web evidence for Persistent Data Engineer interviews and maps it to the Revature Persistent Snowflake_MSFabric curriculum.

## Evidence hierarchy
- **A — Directly reported:** a candidate explicitly describes the question/interview.
- **B — Multiple/recent reported pattern:** repeated across reports or a strong current interview guide.
- **C — Track prediction:** strongly supported by the user's curriculum and current Snowflake/Fabric role requirements, but not confirmed as asked.
- **D — General preparation:** useful knowledge without Persistent-specific evidence.

## Strongest current evidence

### 1. Revature → Persistent fresher pathway
A recent Glassdoor report explicitly describes a Revature-to-Persistent fresher process: assessment, technical interview, Revature training, weekly coding/MCQ/SQL assessments, weekly interviews, then Persistent final assessment/interview focused mainly on training, coding, SQL, technical discussion, resume, and projects. Treat this as candidate evidence rather than official company policy. [Source: Glassdoor result crawled 2026-09-09.]

### 2. Recent hands-on Data Engineer report
A recent Persistent interview report describes this sequence:
- project/end-to-end pipeline discussion;
- Python duplicate removal and second-highest number;
- SQL duplicate detection, RANK vs DENSE_RANK, latest record with ROW_NUMBER;
- Snowflake external stage, file format, COPY, MERGE, QUALIFY, Streams/CDC;
- PySpark null checks, groupBy and RDD map.

This is the single strongest evidence match for this curriculum because it overlaps Python + SQL + Snowflake + PySpark directly.

### 3. Another recent Persistent Data Engineer report
A separate report describes:
- employee salary greater than direct manager;
- weekly critical-order analytics;
- nested JSON flattening with PySpark;
- ADF + Databricks + ADLS architecture;
- dimensional modeling and fact/dimension design;
- narrow vs wide transformations;
- schema evolution;
- SCD Type 2 in Spark;
- Spark optimization;
- Bronze/Silver/Gold;
- production/managerial scenarios.

### 4. Current Persistent Snowflake role signal
A current Persistent Snowflake Data Engineer listing emphasizes scalable data integration/analytics, Snowflake, PySpark/Python, SQL, ETL/data ingestion, data quality, performance and reliability. The listing is for an experienced role, so use it to understand technology priorities, not as a prediction of fresher difficulty.

## What this means for this user's preparation

### P0 — must master
1. SQL window functions
2. SQL joins/subqueries/CTEs/aggregations
3. Python fundamentals and coding
4. PySpark DataFrame operations
5. Spark architecture and transformations/actions
6. Snowflake stages, file formats and COPY
7. Snowflake MERGE/upsert
8. Snowflake QUALIFY
9. Snowflake Streams/CDC
10. ETL/ELT
11. Data modeling
12. SCD Type 2
13. Spark optimization basics
14. Medallion architecture
15. Project explanation

### P1 — very important for this specific curriculum
- Snowflake micro-partitions
- pruning
- clustering
- warehouse sizing/auto-suspend
- cache layers
- semi-structured VARIANT/FLATTEN
- Time Travel / Fail-safe
- zero-copy cloning
- Snowpark
- dbt models/incremental/snapshots
- OneLake
- Fabric Lakehouse vs Warehouse
- Delta tables
- Fabric Data Factory
- incremental ingestion
- SQL endpoint/T-SQL
- Power BI
- RLS/CLS
- lineage/monitoring/CI-CD

### P2 — prepare after P0/P1
- advanced Scala
- deep Spark memory/GC tuning
- advanced streaming state internals
- advanced multi-cloud design
- obscure dbt internals

## Critical distinction
The current public interview reports are mostly for Data Engineer roles and include experienced candidates. The user's situation is different: Revature training for a Persistent Snowflake_MSFabric track. Therefore, we should expect strong testing of training material, coding, SQL, projects and fundamentals, while advanced production scenarios remain possible but should not be treated as guaranteed.

## Sources
- Persistent interview report: https://www.linkedin.com/posts/anshu-kumar-987381142_dataengineer-snowflake-sql-activity-7448582660375076864-5r36
- Persistent interview report: https://www.linkedin.com/posts/samrat-ashok-ak_dataengineering-interviewexperience-sql-activity-7405874595129372672-nCxM
- Persistent Data Engineer interview guide: https://dataford.io/interview-guides/persistent-systems/data-engineer
- Persistent interview reports / Revature pathway: https://www.glassdoor.co.uk/Interview/Persistent-Systems-Software-Developer-Interview-Questions-EI_IE150639.0,18_KO19,37.htm
- Persistent Snowflake Data Engineer role: https://in.linkedin.com/jobs/view/snowflake-data-engineer-at-persistent-systems-4455882020
