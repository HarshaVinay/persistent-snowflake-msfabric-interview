# Persistent Data Engineer — Web Research Update (September 2026)

## Research date
September 9, 2026

## Evidence reviewed
This update uses recent Persistent interview reports and fresher discussions. Sources are treated as evidence, not guarantees.

### Strong recurring pattern
Recent reports repeatedly show a sequence around **Python → SQL → PySpark/Spark → Snowflake/cloud → project discussion**. A recent Persistent hands-on report describes an end-to-end pipeline discussion followed by Python coding, SQL window/duplicate/latest-record problems, Snowflake loading concepts, and PySpark questions. citeturn0search0turn0search8

### Directly reported topics
- Python duplicate removal and second-highest number
- SQL duplicate detection
- `RANK` vs `DENSE_RANK`
- `ROW_NUMBER` for latest records
- Snowflake external stages/file formats/COPY/MERGE/QUALIFY
- Snowflake Streams/CDC
- PySpark null handling/groupBy/RDD map
- SQL employee-vs-manager salary
- Nested JSON parsing/flattening in PySpark
- ADF + Databricks + ADLS pipeline design
- Dimensional modeling
- Narrow vs wide Spark transformations
- Schema evolution
- SCD Type 2
- Spark optimization
- Bronze/Silver/Gold

These are directly supported by candidate reports and should be tagged A/B in the question bank rather than treated as generic guesses. citeturn0search0turn0search2

### Snowflake signal
A Persistent Data Engineer report explicitly identifies **Snowflake + PySpark + zero-copy cloning + a third-highest-salary window-function problem**. citeturn0search5

### Fresher signal
A February 2026 fresher/0–2 YOE discussion says the recruiter expected emphasis on SQL, cloud and core data engineering, with commenters highlighting window functions, joins, subqueries, ETL/ELT and Databricks. This is useful but anecdotal. citeturn0reddit14turn0reddit15

### Current Persistent interview variability
Persistent's overall interview reports show multiple technical and client/managerial stages depending on role. Therefore we should not assume one fixed interview structure. citeturn0search7

## Updated priority for the user's Snowflake_MSFabric track

### P0
1. SQL window functions and analytical SQL
2. Python fundamentals/coding
3. PySpark DataFrame operations
4. Spark architecture, transformations, shuffle and optimization
5. Snowflake loading/stages/COPY/MERGE/QUALIFY
6. Snowflake architecture/performance
7. Data modeling and SCD
8. ETL/ELT and incremental pipelines
9. Project deep dive
10. Medallion architecture

### P1
- ADF/Azure
- Snowpark
- dbt
- Snowflake security/RBAC/masking/RLS
- Spark streaming
- schema evolution/data quality
- Fabric OneLake/Lakehouse/Warehouse/Data Factory

### P2
- Scala details beyond Spark-relevant fundamentals
- BigQuery specifics
- advanced Power BI/DAX
- obscure framework internals

## Important distinction
The user's curriculum is authoritative for what must be learned. Web reports determine interview likelihood, not syllabus membership. Microsoft Fabric is therefore P0/P1 for this user's specialization even where public Persistent interview reports do not explicitly mention Fabric.

## Sources
- Persistent Data Engineer interview experience — Anshu Kumar: https://www.linkedin.com/posts/anshu-kumar-987381142_dataengineer-snowflake-sql-activity-7448582660375076864-5r36
- Persistent Data Engineer interview experience — Samrat Ashok Chakkarawarthy: https://www.linkedin.com/posts/samrat-ashok-ak_dataengineering-interviewexperience-sql-activity-7405874595129372672-nCxM
- Senior Data Engineer interview experience — Sumit Mittal: https://www.linkedin.com/posts/bigdatabysumit_applied-for-senior-data-engineer-walked-activity-7451974278096306176-nz4e
- Persistent Data Engineer report — Glassdoor: https://www.glassdoor.com/Interview/Sql-Snowflake-Pyspark-Zero-copy-cloning-in-snowflake-Third-highest-salary-sql-question-using-window-function-QTN_8629636.htm
- Persistent Data Engineer guide: https://dataford.io/interview-guides/persistent-systems/data-engineer
- Fresher discussion: https://www.reddit.com/r/developersIndia/comments/1qxh0g7/persistent_systems_data_engineer_interview_sqlaws/
