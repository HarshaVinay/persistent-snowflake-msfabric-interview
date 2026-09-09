# Azure / ADLS / Data Factory Complete Master Notes

## Cloud service models
IaaS = infrastructure, PaaS = managed platform, SaaS = complete application/service.

## Azure data architecture mental model
`source systems → ADF/Fabric pipelines → ADLS/OneLake → Spark/SQL transformation → Snowflake/Fabric Warehouse → Power BI`.

## ADLS Gen2
Cloud object storage designed for large-scale analytics workloads. Think storage layer, not transformation engine.

## Azure Data Factory
ADF is an orchestration/data-integration service. A pipeline groups activities; linked services describe connection information; datasets describe data structures/locations; Integration Runtime provides the compute/connectivity mechanism for activities.

## Triggers
Know schedule/time-based, event-based and tumbling/periodic scheduling concepts as applicable. The important interview point is **what starts a pipeline and how parameters are supplied**.

## Copy Activity
Moves data between supported source and target systems. The important engineering concerns are throughput, mappings, partitioning/parallelism, retries, monitoring and failure handling.

## Incremental loading
Common patterns:
- watermark on `last_modified`
- CDC
- date/partition window
- source sequence/ID

Example logic:
`read watermark → extract changes → validate → write stage → merge target → advance watermark only after successful commit`.

## Metadata-driven pipelines
Store configuration such as source table, target, watermark column and load strategy in metadata instead of hardcoding each pipeline.

## Failure handling
Use retries for transient failures, capture error details, isolate bad records when needed, and make downstream writes idempotent. Never advance a watermark before successful target persistence.

## Security
Prefer managed identity/service principals and least privilege. Do not embed secrets in notebooks or pipeline code.

## ADF + Databricks
Typical pattern:
`ADF orchestrates → Databricks notebook transforms → curated storage/table`.
ADF handles scheduling/dependency orchestration; Spark handles distributed transformations.

## Interview scenario
**ADF pipeline loads the same day twice.**
Answer: use deterministic batch/business keys, watermark or run identifiers, stage data before merge, and make the final write idempotent.

## What Persistent may probe
Historical Persistent reports include Azure service knowledge, ADF triggers/Integration Runtime, pipeline design, duplicates, schema evolution and Databricks/ADLS architecture. Treat individual reports as evidence, not guarantees.
