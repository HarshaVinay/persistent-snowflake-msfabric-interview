# Persistent Systems Data Engineering Interview Research — Executive Summary

## Target
Revature-trained fresher preparing for a Persistent Systems client interview for a Data Engineering / Snowflake_MSFabric track.

## Main finding
The most defensible preparation strategy is to focus on the intersection of:
1. The user's actual Revature Persistent Snowflake_MSFabric curriculum.
2. Candidate-reported Persistent interview questions.
3. The user's real projects.

Public interview evidence is heterogeneous by role, seniority, client assignment and interview round. It is evidence, not a guarantee of the exact interview.

## Strongest recurring technical themes
### Tier 1
- SQL/window functions/joins
- PySpark/Spark fundamentals
- Spark optimization
- Data modeling and SCD
- Project/end-to-end pipeline discussion
- Azure/ADF concepts

### Tier 2
- Databricks/Delta
- Schema evolution
- Data skew
- Repartition/coalesce
- Medallion Architecture
- Incremental loading/data quality

### Track-specific high priority
Because this is the user's Snowflake_MSFabric track:
- Snowflake architecture/performance/loading/security
- Snowpark
- dbt
- OneLake/Lakehouse/Warehouse
- Fabric Data Factory
- Fabric Spark/PySpark
- T-SQL/star schema
- Power BI integration
- RLS/CLS/lineage/CI-CD

These track-specific items are often **C — high-probability predictions**, not confirmed historical questions, unless a candidate report explicitly supports them.

## Fresher caution
Experienced candidate reports contain deeper production scenarios such as multi-terabyte processing, executor OOM, advanced skew mitigation and detailed system design. Those are useful practice but should not be treated as the baseline for a fresher.

## Interview behavior to optimize
The candidate should be able to:
- explain concepts in 30–60 seconds;
- solve common SQL/Python/PySpark coding tasks;
- reason through production-style scenarios;
- defend project technology choices;
- distinguish implemented experience from training knowledge.
