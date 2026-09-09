# Azure Data Engineering — ADLS & ADF

## ADLS Gen2
Azure Data Lake Storage Gen2 is cloud storage designed for large-scale analytics. Think of it as durable storage for raw/processed data, not the transformation engine itself.

## ADF / Fabric Data Factory mental model
```text
Source
  ↓
Linked service / connection
  ↓
Dataset or source definition
  ↓
Pipeline
  ↓
Activity
  ↓
Destination
```

## Pipeline
A pipeline is an orchestrated workflow containing activities.

## Common activities
- Copy Activity for movement/ingestion.
- Lookup for metadata/control information.
- Execute SQL/Notebook-style activities depending on platform integration.

## Integration Runtime
Integration Runtime provides the compute/connectivity infrastructure used by Azure Data Factory/Synapse pipelines to move and process data according to the selected activity/connectivity pattern.

## Triggers
Know:
- schedule trigger;
- event-based trigger;
- tumbling-window style scheduling concept.

## Parameters
Use parameters for reusable pipelines, such as:
```text
source_path
load_date
table_name
watermark
```
Avoid hard-coding environment-specific values.

## Incremental pipeline
```text
Metadata/control table
      ↓
Read last successful watermark
      ↓
Source query/filter
      ↓
Copy new/changed data
      ↓
Validate
      ↓
Curated write
      ↓
Update watermark only after success
```

## Failure handling
- retries for transient failures;
- alerts/logging;
- idempotent writes;
- quarantine bad data;
- clear dependency ordering;
- rerun from a safe boundary.

## Interview question
**ADF vs Databricks?**
ADF is primarily orchestration/data movement; Databricks/Spark is compute for distributed transformation. They are complementary rather than direct replacements.
