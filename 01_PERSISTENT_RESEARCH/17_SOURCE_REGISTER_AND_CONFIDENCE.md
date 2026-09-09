# Persistent Research — Canonical Source Register

**Last reviewed:** 2026-09-09

## Purpose
This is the canonical research index. Dated research notes are historical snapshots; this file records the sources that should drive current study decisions.

## Source hierarchy

### Tier 1 — Official product documentation
Use for current technical truth.

**Snowflake**
- Micro-partitions & clustering: https://docs.snowflake.com/en/user-guide/tables-clustering-micropartitions
- Time Travel: https://docs.snowflake.com/en/user-guide/data-time-travel
- Time Travel & Fail-safe overview: https://docs.snowflake.com/en/user-guide/data-availability
- Fail-safe: https://docs.snowflake.com/en/user-guide/data-failsafe
- CREATE CLONE: https://docs.snowflake.com/en/sql-reference/sql/create-clone
- Cloning considerations: https://docs.snowflake.com/en/user-guide/object-clone
- Streams and Tasks: https://docs.snowflake.com/en/user-guide/data-pipelines-intro

**Microsoft Fabric**
- OneLake overview: https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview
- OneLake documentation: https://learn.microsoft.com/en-us/fabric/onelake/
- Lakehouse overview: https://learn.microsoft.com/en-us/fabric/data-engineering/lakehouse-overview
- Medallion architecture: https://learn.microsoft.com/en-us/fabric/onelake/onelake-medallion-lakehouse-architecture
- Data storage options: https://learn.microsoft.com/en-us/fabric/fundamentals/store-data
- Direct Lake: https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-how-it-works
- Direct Lake security: https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-security-integration
- OneLake security: https://learn.microsoft.com/en-us/fabric/onelake/security/get-started-security
- OneLake RLS/CLS: https://learn.microsoft.com/en-us/fabric/onelake/security/row-level-security
- Fabric Data Factory: https://learn.microsoft.com/en-us/fabric/data-factory/

### Tier 2 — Persistent company / role evidence
Use for current role alignment and technology priorities.
- Persistent Data & Analytics: https://www.persistent.com/services/data-and-analytics/
- Current Persistent Data Engineer/Snowflake roles should be checked for the exact assignment and stack when the target posting is known.

### Tier 3 — Candidate interview reports
Use for question-pattern detection, never as guaranteed prediction.
- Karthik K. — Persistent Data Engineer: https://www.linkedin.com/posts/karthik-kondpak_persistent-systems-data-engineer-interview-activity-7325033767062962177-YA1_
- Ritik Agarwal — Azure Data Engineer: https://www.linkedin.com/posts/ritik-agarwal-3b061a156_azuredataengineer-persistentsystems-dataengineering-activity-7355429751953510402-2cdx
- Samrat Ashok — Data Engineer: https://www.linkedin.com/posts/samrat-ashok-ak_dataengineering-interviewexperience-sql-activity-7405874595129372672-nCxM
- Sumit Mittal — Senior Data Engineer: https://www.linkedin.com/posts/bigdatabysumit_applied-for-senior-data-engineer-walked-activity-7451974278096306176-nz4e
- Rabi Sankar Mahata — Persistent Data Engineer: https://www.linkedin.com/posts/rabi-sankar-mahata_persistent-systems-%F0%9D%97%BC%F0%9D%97%B3%F0%9D%97%B3%F0%9D%97%B2%F0%9D%97%BF%F0%9D%97%B2%F0%9D%97%B1-%F0%9D%97%BA%F0%9D%98%86-%F0%9D%97%B3-activity-7485646708756889600-4E9F
- Persistent Snowflake/PySpark/SQL Glassdoor report: https://www.glassdoor.com/Interview/Sql-Snowflake-Pyspark-Zero-copy-cloning-in-snowflake-Third-highest-salary-sql-question-using-window-function-QTN_8629636.htm

### Tier 4 — Community/fresher context
- Revature → Persistent discussion: https://www.reddit.com/r/Revature/comments/1qkk29g/anyone_interviewed_with_persistent_systems_via/
- Fresher/0–2 YOE discussion: https://www.reddit.com/r/developersIndia/comments/1qxh0g7/persistent_systems_data_engineer_interview_sqlaws/

## Confidence labels
- **A — Directly reported:** candidate explicitly says it was asked in a Persistent interview.
- **B — Reported, experienced level:** reported at Persistent but mainly from experienced candidates.
- **C — High probability:** strong overlap of curriculum + role + recurring reports, but not confirmed.
- **D — General:** useful preparation without Persistent-specific evidence.

## Evidence rules
1. Never call a C/D question “asked by Persistent.”
2. Prefer repeated patterns over isolated posts.
3. Preserve candidate experience level and round where available.
4. Official vendor documentation overrides old training material when current platform behavior differs.
5. Candidate reports are not leaked question banks and may contain mistakes.

## Current high-confidence themes
- SQL analytics: window functions, ranking, duplicates, latest-record logic, joins, aggregation.
- Python coding/data manipulation.
- PySpark/Spark: DataFrames, RDDs, joins, partitions, shuffle, skew, schema evolution, optimization, JSON.
- Snowflake: stages, file formats, COPY, MERGE, QUALIFY, Streams/CDC, cloning, performance.
- ETL/ELT, dimensional modeling, SCD, incremental processing.
- Azure/ADF/ADLS architecture.
- Medallion Architecture.
- Project explanation and troubleshooting.

## Current Fabric facts requiring fresh verification
- OneLake is Fabric's unified logical data lake.
- Lakehouse supports file/table storage and SQL/Spark access; Delta is central to Lakehouse storage.
- Medallion architecture is a recommended Fabric design pattern.
- Direct Lake has distinct OneLake and SQL endpoint behavior, including different security/fallback considerations.
- OneLake security includes table/folder, row-level and column-level controls.

## Research maintenance rule
Do not add a dated research file for every minor search. Update this canonical register when a source materially changes the study plan; create a dated snapshot only for a meaningful evidence or platform change.
