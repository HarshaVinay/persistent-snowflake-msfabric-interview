# Persistent Interview Web Research — 2026-09-09

## Key conclusion
The newest public evidence continues to show a strong Data Engineer pattern around **SQL + Python + Spark/PySpark + Snowflake + cloud data engineering + project discussion**.

## Strong recent evidence
A recent Persistent Data Engineer interview report describes an end-to-end pipeline discussion followed by Python, SQL, Snowflake and PySpark hands-on questions. Reported Snowflake topics include external stages, file formats, COPY, MERGE, QUALIFY and Streams/CDC. citeturn0search1

Another Persistent report includes employee-vs-manager SQL, nested JSON flattening with PySpark, Azure Data Factory/Databricks/ADLS design, dimensional modeling, narrow vs wide Spark transformations, schema evolution, SCD Type 2, Spark optimization and Bronze/Silver/Gold architecture. citeturn0search2

A recent Persistent interview guide also emphasizes Python, SQL, PySpark, Snowflake, Azure Data Factory, Medallion Architecture, real-time pipelines, PII masking/encryption and pipeline recovery. Treat this guide as secondary evidence because it is an aggregation rather than a first-person interview report. citeturn0search3

A separate interview report lists Spark cache/persist, map/flatMap/mapPartitions, wide/narrow transformations and skew, plus second-highest salary and PySpark coding. citeturn0search4

A 2026 fresher-oriented Reddit discussion says candidates were told to focus on SQL, AWS and core data-engineering concepts; replies specifically recommended window functions, joins, subqueries, ETL/ELT and Databricks. This is weak evidence but useful for fresher calibration. citeturn0reddit18turn0reddit19

## What this means for this curriculum
### P0
- SQL window functions
- joins/subqueries
- Python basics + coding
- PySpark DataFrame transformations
- Spark fundamentals and optimization
- Snowflake stages/loading/MERGE/QUALIFY/Streams
- ETL/ELT
- data modeling and SCD
- Medallion architecture
- project explanation

### P1
- Snowflake performance/cost
- Snowpark
- dbt
- Azure Data Factory
- Fabric OneLake/Lakehouse/Warehouse
- security/RLS/CLS
- monitoring/recovery

### P2
- deep Scala internals
- obscure Spark memory tuning
- advanced Fabric edge cases
- advanced dbt internals

## Important role/seniority caveat
Some reports are for experienced engineers and should not be copied directly into a fresher prediction. The correct approach is to master the underlying concepts while answering honestly about hands-on exposure. The Snowflake Data Engineer job posting currently visible from Persistent is for a much more experienced role and explicitly asks for Snowflake, PySpark/Python, SQL, ETL/ELT and data quality/performance skills; it is useful as a technology signal, not as evidence of a fresher interview format. citeturn0search9

## Bottom line
For the user's Revature → Persistent track, the preparation center of gravity should remain:

`SQL → Python → PySpark/Spark → Snowflake → Data Engineering/Modeling → Projects → Azure/Fabric`

Fabric must still be prepared deeply because it is explicitly in the user's curriculum, even though the latest public Persistent reports contain fewer Fabric-specific questions than Snowflake/Spark questions.
