# SCD / CDC / Incremental Loading Master Notes

## Why this matters
Persistent interview reports repeatedly use SCD, schema evolution and pipeline scenarios. These are also core topics in the user's curriculum.

## SCD
### Type 0
Keep original value.
### Type 1
Overwrite current value; no history.
### Type 2
Create a new dimension version and preserve old history.

Typical Type 2 columns:
```text
surrogate_key
business_key
attributes...
effective_start_date
effective_end_date
is_current
```

## SCD2 example logic
```text
Incoming change for customer C1
        ↓
Find current C1
        ↓
Close old row (is_current=false, end date)
        ↓
Insert new row (new surrogate key, current=true)
```

## CDC
Change Data Capture identifies inserts/updates/deletes from a source so downstream processing can be incremental.

## Incremental loading
Full load processes all source records.
Incremental load processes only new/changed records.

Common keys:
- updated_at watermark
- monotonically increasing ID
- source CDC log/LSN
- vendor-specific change tracking

## Idempotency
A rerun should not create duplicates or corrupt state. Use deterministic business keys, MERGE/upsert logic, checkpoints/watermarks and controlled writes.

## Late-arriving data
Do not assume event time and arrival time are identical. Use an overlap window, reprocessing strategy or CDC approach where required.

## Schema evolution
New source columns should be handled deliberately. Separate compatible additions from breaking type/semantic changes.

## Interview questions
- Explain SCD1 vs SCD2.
- Implement SCD2 in Spark/Delta.
- How do you process only changed rows?
- What happens if a pipeline reruns?
- How do you handle late records?
- How do you react to a new JSON field?

## Project connection
Cricket project can be used to explain incremental/orchestration concepts. Snowflake and dbt provide natural MERGE/incremental/snapshot implementations; Fabric Lakehouse provides Delta-based patterns.
