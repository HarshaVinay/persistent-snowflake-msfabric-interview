# dbt Master Notes — Persistent Snowflake_MSFabric

## Curriculum coverage
Fundamentals, project structure, models/materializations, sources/seeds, tests, documentation, advanced overview, Snowflake integration, incremental models, snapshots/SCD, monitoring, cost optimization and troubleshooting.

## Mental model
```text
Sources → dbt models → dependencies/DAG → tests/docs → target warehouse
```

dbt primarily handles the transformation/modeling layer; it does not replace the source ingestion system by itself.

## Core objects
- `model`: SQL transformation.
- `source`: declared upstream data source.
- `seed`: version-controlled CSV data loaded by dbt.
- `ref()`: creates model dependency and resolves relation names.
- materialization: how a model is represented in the target (for example view/table/incremental).
- tests: validate assumptions such as uniqueness, not-null and relationships.
- snapshots: preserve changes over time for SCD-style history.

## Incremental model
Goal: process only new/changed rows. Requirements: reliable change key/watermark, deterministic logic, handling of late changes, and idempotent reruns.

## Snowflake
dbt can use Snowflake as the transformation target. Explain why this fits ELT: land data, then use warehouse compute for SQL transformations.

## Interview questions
- What is dbt and why use it?
- `ref()` vs hard-coded table names.
- View vs table vs incremental.
- What is a snapshot?
- How can snapshots support SCD2?
- How do dbt tests improve data quality?
- How do you troubleshoot an incremental model?

## Curriculum depth
Advanced dbt is explicitly a brief overview in the user's curriculum. Prioritize fundamentals, Snowflake integration, incremental models and snapshots over obscure internals.
