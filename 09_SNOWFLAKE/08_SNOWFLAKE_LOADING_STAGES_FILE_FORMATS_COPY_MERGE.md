# Snowflake Loading, Stages, File Formats, COPY & MERGE

## Loading mental model
```text
Source files
   ↓
Stage
   ↓
COPY INTO
   ↓
Target table
   ↓
Validation / transformation / MERGE
```

## Stages
A stage is a location used to access files for loading/unloading.

Know:
- user stage;
- table stage;
- named internal stage;
- external stage.

External stages can reference supported cloud storage such as S3, Azure storage or Google Cloud Storage.

## File formats
Know CSV, JSON, Parquet, Avro and ORC at interview level.

General guidance:
- CSV: simple and interoperable, but larger and schema-light.
- JSON: flexible/semi-structured.
- Parquet: columnar and strong for analytical workloads.
- Avro: schema-oriented serialization.
- ORC: columnar analytical format.

## COPY INTO
Typical pattern:
```sql
COPY INTO target_table
FROM @my_stage
FILE_FORMAT = (TYPE = CSV SKIP_HEADER = 1)
ON_ERROR = 'CONTINUE';
```

Know the purpose of `ON_ERROR`, file format definitions and validation options rather than memorizing every syntax variation.

## Error handling
A pipeline must decide whether to stop the load, continue, or skip problematic files/records. Quarantine invalid data when business requirements require traceability.

## MERGE
Used for matched/unmatched conditional insert/update logic.

Conceptual pattern:
```sql
MERGE INTO target t
USING source s
ON t.business_key = s.business_key
WHEN MATCHED THEN UPDATE SET ...
WHEN NOT MATCHED THEN INSERT (...)
VALUES (...);
```

Useful for incremental upserts and SCD patterns.

## COPY + MERGE pattern
```text
Files
 ↓
Stage
 ↓
COPY to raw/staging table
 ↓
Deduplicate / validate
 ↓
MERGE into curated table
```

## Interview questions
- Internal vs external stage?
- How do you load Parquet/JSON?
- How do you handle bad files?
- Why stage data before loading?
- COPY vs MERGE?
- How would you make an incremental load idempotent?
