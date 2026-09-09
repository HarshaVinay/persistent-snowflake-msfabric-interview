# ETL, ELT, Incremental Loading & CDC

## ETL
Extract → Transform → Load.
Transform before loading to the target.

## ELT
Extract → Load → Transform.
Land data first, then use target compute for transformations.

Cloud warehouses/lakehouses often make ELT attractive because compute and storage are separated or can scale independently, but architecture must be chosen from workload requirements.

## Full load
Reprocess the complete source dataset each run.
Simple but can be expensive and slow.

## Incremental load
Process only new or changed records.
Common controls:
- watermark timestamp
- monotonically increasing ID
- source change version
- CDC log
- partition/date boundary

## Idempotency
A rerun should not create incorrect duplicates or inconsistent state.
Typical techniques:
- deterministic business keys
- `MERGE`/upsert
- deduplication before write
- checkpoints
- batch/run identifiers

## CDC
Change Data Capture identifies inserts, updates and deletes occurring at a source.
CDC can be implemented with database logs, timestamps, change tables or platform-native change tracking.

## Watermark example
```text
last_successful_timestamp = T
↓
read source WHERE updated_at > T
↓
validate/deduplicate
↓
write
↓
commit new watermark
```

Do not advance the watermark before the write succeeds.

## Failure handling
A production incremental pipeline should define what happens when:
- extraction partially succeeds;
- transformation fails;
- destination write fails;
- the same batch is retried;
- source records arrive late.

## Interview answer
“For a large recurring dataset, I would prefer incremental ingestion using a reliable change boundary. I would land raw data, validate and deduplicate it, then use an idempotent merge/upsert into the curated layer. I would persist the last successful watermark only after the downstream write succeeds, so a retry can safely reprocess the failed boundary.”
