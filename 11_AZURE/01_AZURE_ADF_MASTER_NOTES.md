# Azure / Data Factory Master Notes

## Curriculum coverage
Cloud service models, AWS/Azure/GCP overview, pricing/components/architecture/benefits/challenges; Fabric Data Factory, pipelines/activities, batch/incremental ingestion, Copy Activity/Dataflows Gen2, parameterization/scheduling.

## Service models
IaaS = infrastructure; PaaS = managed platform; SaaS = complete application/service.

## Azure data-engineering mental model
```text
Source
 ↓
ADLS / landing
 ↓
ADF pipeline
 ↓
Spark/Databricks transformation
 ↓
Curated data
 ↓
Snowflake / Fabric / BI
```

## ADF concepts
- Pipeline: workflow container.
- Activity: unit of work.
- Linked service: connection definition.
- Dataset: data structure/location reference.
- Integration Runtime: compute/connectivity infrastructure used by ADF activities.
- Trigger: starts a pipeline based on schedule/event/manual conditions.
- Parameter: runtime configuration.

## Copy Activity
Used to move data between sources/sinks. For large workloads, think about partitioning, parallelism, integration runtime, file sizing and source/sink limits.

## Incremental loading
Common pattern:
```text
Source watermark/CDC
 ↓
Lookup latest processed value
 ↓
Copy only changed/new rows
 ↓
Transform/merge
 ↓
Persist new watermark
```
Make reruns safe and account for late-arriving changes.

## Failure handling
Use retries, failure paths, logging/monitoring, checkpoints/watermarks and idempotent writes. Do not rely on "rerun everything" when that can duplicate data.

## Schema drift
Detect unexpected/new fields. Decide whether to allow compatible evolution, quarantine incompatible records, or update target schema through controlled deployment.

## Security
Prefer managed identity/service principals and least privilege where supported. Keep secrets out of code.

## Interview scenarios
- Configure ADF triggers and Integration Runtime.
- Parallel copy of files.
- Build metadata-driven pipeline.
- Resume after failure.
- Incremental pipeline with watermark.
- ADF + Databricks + ADLS design.

## Persistent relevance
Recent Persistent candidate reports repeatedly mention Azure services, ADF triggers/IR, parallel copy, Databricks/ADLS pipeline design, schema evolution and data quality.
