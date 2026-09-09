# Fabric Data Factory + Warehouse + Power BI Master Notes

## Data Factory in Fabric
Pipeline orchestration for ingestion/transformation workflows. Curriculum topics: pipelines, activities, Copy Activity, Dataflows Gen2, batch/incremental ingestion, parameterization and scheduling.

## Copy Activity
Move data from source to target. Design for throughput, partitioning/parallelism, retries, monitoring and parameterized paths.

## Dataflows Gen2
Low-code transformation/ingestion option. Use when visual transformation is appropriate; use notebooks/Spark for code-heavy distributed processing.

## Pipeline design
```text
Trigger
 ↓
Ingest
 ↓
Validate
 ↓
Transform
 ↓
Load curated layer
 ↓
Quality check
 ↓
Publish/notify
```

## Warehouse
Use T-SQL-oriented analytics over curated structured data. Build facts/dimensions, surrogate keys as needed, and star schema for BI.

## Lakehouse SQL endpoint
Provides SQL access to Lakehouse table data for analytics. Keep Spark/notebook engineering and SQL serving responsibilities conceptually separate.

## Star schema
```text
             dim_customer
                  |
dim_date — fact_sales — dim_product
                  |
             dim_store
```
Facts contain measures and foreign keys; dimensions provide descriptive context.

## Power BI
Connect reports/semantic models to curated analytical data. Know relationships, measures, semantic models and RLS.

## Direct Lake
Current Microsoft documentation describes Direct Lake semantic models loading required columns from Delta tables in OneLake on demand. Direct Lake on OneLake is distinct from Direct Lake on SQL endpoints, where DirectQuery fallback can occur for some SQL-security situations. citeturn141865search6

## RLS
Restrict rows based on user/context. Design the model so security logic is predictable and test it with representative identities.

## Interview scenario
"Build a Fabric sales analytics solution."
Answer: sources → Data Factory ingestion → Bronze → PySpark cleaning → Silver → dimensional Gold → Warehouse/semantic model → Power BI. Add incremental processing, quality checks, monitoring, security and cost controls.
