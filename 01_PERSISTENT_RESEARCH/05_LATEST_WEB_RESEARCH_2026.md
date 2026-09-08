# Latest Persistent Interview Web Research — 2026

## Purpose
This file records fresh web evidence and separates reported questions from inference. It should be updated when new credible reports appear.

## 1. Revature → Persistent fresher evidence
A July 2026 Glassdoor report describes a fresher/off-campus Revature pathway: assessment, technical interview, Revature training, weekly coding/MCQ/SQL assessments and interviews, followed by Persistent final assessments/interviews. The candidate states that the final stage was mostly focused on what was learned during the training, coding, SQL queries, technical interview, then HR. **Evidence: A for this candidate's experience; not a universal guarantee.**

Source: https://www.glassdoor.co.uk/Interview/Persistent-Systems-Software-Developer-Interview-Questions-EI_IE150639.0,18_KO19,37.htm

A January 2026 Reddit discussion about Revature → Persistent similarly says candidates were trained for the particular Persistent opening and that the final interview would be based largely on what was studied during training. This is community evidence, not official policy.

Source: https://www.reddit.com/r/Revature/comments/1qkk29g/anyone_interviewed_with_persistent_systems_via/

## 2. New Persistent Data Engineer report — very relevant to this curriculum
A recent LinkedIn report describes a Persistent Data Engineer interview with an end-to-end pipeline discussion: Source → Azure → Synapse/PySpark → Snowflake. The interviewer tested Python logic, SQL window functions, Snowflake staging/loading/MERGE/Streams, and PySpark transformations.

Reported Python tasks included removing duplicates and sorting without using a set, and finding the second-highest number. SQL included duplicate detection, RANK vs DENSE_RANK, and latest-record filtering with ROW_NUMBER. Snowflake included external stages, COPY, file formats, MERGE, QUALIFY and Streams. PySpark included null filtering, groupBy/count and an RDD map operation.

Source: https://www.linkedin.com/posts/anshu-kumar-987381142_dataengineer-snowflake-sql-activity-7448582660375076864-5r36

**Classification:** A — directly reported Persistent interview experience. Because this is a recent report and closely matches the user's Snowflake_MSFabric curriculum, it materially increases priority for these topics.

## 3. Repeated SQL + PySpark + Azure pattern
Another Persistent Data Engineer report lists:
- employee salary greater than direct manager;
- users exceeding a weekly critical-order threshold;
- flattening nested JSON with PySpark;
- cost-efficient Azure ADF + Databricks + ADLS pipeline;
- dimensional modeling and a sales fact table;
- narrow vs wide Spark transformations;
- schema evolution;
- SCD Type 2 in Spark;
- terabyte-scale Spark optimization;
- Bronze/Silver/Gold architecture.

Source: https://www.linkedin.com/posts/samrat-ashok-ak_dataengineering-interviewexperience-sql-activity-7405874595129372672-nCxM

**Classification:** A/B — reported Persistent experience, but the candidate is not a fresher. Use as evidence for technical themes, not exact expected depth.

## 4. Azure Data Engineer reports
Persistent Azure Data Engineer reports include:
- Synapse vs Azure SQL performance tuning;
- deadlocks;
- metadata-driven ingestion;
- data lineage/impact analysis;
- large-fact-table partitioning;
- RDD/DataFrame/Dataset;
- PySpark joins;
- schema evolution;
- CSV → null filtering → Parquet coding;
- memory management for large files;
- end-to-end pipeline explanation;
- ADF triggers and Integration Runtime;
- duplicate handling;
- window functions;
- slow SQL optimization;
- T-SQL procedure error handling.

Sources:
- https://www.linkedin.com/posts/aditya-kumar-246b60195_persistent-systems-for-azure-data-engineer-activity-7355881932938768384-nUjT
- https://www.linkedin.com/posts/ritik-agarwal-3b061a156_azuredataengineer-persistentsystems-dataengineering-activity-7355429751953510402-2cdx

**Classification:** A/B.

## 5. Databricks/Spark optimization evidence
A recent Persistent Senior Data Engineer report asks about:
- min/max/average salary by department;
- 3-day moving average;
- total flight delay by flight/week;
- optimizing slow Spark jobs in Databricks;
- small-file problem;
- choosing partition counts;
- processing 5 TB;
- project optimization;
- huge CSV loading;
- deployment challenges;
- end-to-end architecture and data volume.

Source: https://www.linkedin.com/posts/bigdatabysumit_applied-for-senior-data-engineer-walked-activity-7451974278096306176-nz4e

**Classification:** B — useful but senior-level. Extract concepts, not expected senior depth.

## 6. Snowflake-specific signal
The latest direct Snowflake/Persistent report is especially important because it tests the exact combination of:
- Snowflake stages;
- file formats;
- COPY;
- MERGE;
- QUALIFY;
- Streams;
- SQL window functions;
- PySpark.

This means Snowflake should not be treated as a purely theoretical module. For this preparation, loading + MERGE + deduplication + Streams/CDC should be elevated alongside architecture/performance.

## 7. Current Persistent role signal
Current Persistent Data Engineer roles continue to emphasize modern data engineering stacks including Snowflake, SQL, Python/PySpark, ELT, modeling and data quality. This supports prioritizing the user's Snowflake_MSFabric specialization, but job postings do not prove what the September interview will ask.

## 8. Research conclusion
The strongest current evidence says the preparation should center on:

**Python coding → SQL → PySpark → ETL/ELT → dimensional modeling/SCD → Azure/ADF → Snowflake loading/MERGE/Streams → Spark optimization → project architecture.**

For this specific curriculum, add **Fabric/OneLake/Lakehouse/Medallion/Data Factory/Warehouse/Power BI/governance** as P0 curriculum preparation even though public historical interview evidence for Fabric-specific questions is weaker.

## Evidence discipline
Do not state that a question is “definitely asked” unless the source explicitly reports it. Experienced-candidate reports should not be used to predict exact fresher depth.
