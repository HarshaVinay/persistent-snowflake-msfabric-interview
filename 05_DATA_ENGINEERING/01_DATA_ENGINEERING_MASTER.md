# Data Engineering Master

## Core chain
Sources → ingestion → raw/bronze → cleaning/conformance/silver → business-ready/gold → warehouse/semantic layer → BI/consumers.

## ETL vs ELT
ETL transforms before loading into target. ELT loads raw/staged data first and transforms using target compute. Choose based on scale, tooling, governance and workload.

## Lake vs warehouse vs lakehouse
Lake: inexpensive flexible storage for varied data. Warehouse: structured analytical serving, SQL/model-centric. Lakehouse: combines lake storage with table/transaction/query capabilities; Fabric Lakehouse uses Delta and supports Spark + SQL. citeturn969057search0

## OLTP vs OLAP
OLTP: operational writes, normalized models, low-latency transactions. OLAP: analytical scans, aggregations, history, dimensional models.

## Modeling
Always define **grain** first. Facts contain measurable events; dimensions describe business entities. Star schema keeps dimensions around a central fact. Snowflake schema normalizes dimensions further.

## SCD
Type 1 overwrites history. Type 2 preserves versions using surrogate keys/effective dates/current flag. Be able to implement Type 2 conceptually with MERGE + expire/insert logic.

## Incremental loading
Use watermark/change timestamp, CDC, source version or business key. Make the pipeline idempotent and safe to rerun.

## Data quality
Schema/type validation, null checks, uniqueness, referential integrity, accepted ranges, duplicate detection, freshness, row-count reconciliation and business-rule tests.

## Pipeline reliability
Retries, checkpointing where applicable, quarantine/DLQ, audit columns, idempotency, atomic/transactional target writes, alerts, lineage and restart strategy.

## Design questions
- Design daily ingestion from CSV/API/database.
- Convert a full load to incremental.
- Explain how you would recover after a failed pipeline.
- How would you handle schema evolution and bad records?
