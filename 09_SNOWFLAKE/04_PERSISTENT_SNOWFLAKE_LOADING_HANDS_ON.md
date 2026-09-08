# Snowflake — Loading Hands-on Interview Guide

## P0: External stage → table

Be able to explain the full chain:

**Source file → external stage → file format → COPY INTO → target table → validation**

Know the purpose of each component rather than memorizing syntax alone.

## File formats

Prepare:
- CSV
- JSON
- Parquet
- Avro
- ORC
- delimiter/header/quote/escape concepts
- schema handling
- error handling

## COPY INTO

Be able to explain:
- loading from a stage into a table
- file format association
- validation/error handling
- duplicate/reload considerations
- how loading fits into an ETL/ELT pipeline

## MERGE

Know the conceptual pattern:

`source + business key → matched update / not-matched insert`

Interview follow-ups:
- What happens when source contains duplicate business keys?
- How do you make the operation deterministic?
- How does MERGE support incremental processing?
- How would you implement SCD Type 2 instead of a simple upsert?

## QUALIFY

Know why Snowflake's `QUALIFY` is useful with window functions, especially for deduplication/latest-record logic.

Canonical pattern:

```sql
SELECT *
FROM target
QUALIFY ROW_NUMBER() OVER (
    PARTITION BY business_key
    ORDER BY updated_at DESC
) = 1;
```

## Streams / CDC

Know:
- what a Stream tracks
- INSERT/UPDATE/DELETE change information at a conceptual level
- how Streams support incremental pipelines
- why a downstream task/procedure/process may consume the changes
- why CDC reduces unnecessary full processing

## Zero-copy cloning

Know the concept, benefits, use cases and important storage/cost implications. This has direct Persistent interview evidence.

## Strong evidence

A recent Persistent Data Engineer interview report explicitly lists external-stage access, file formats, COPY, MERGE, QUALIFY and Streams/CDC as hands-on Snowflake topics.

## Important distinction

Do not claim that every Snowflake topic in the curriculum is historically confirmed as a Persistent question. Treat:
- stage/COPY/MERGE/QUALIFY/Streams as **strong reported evidence**;
- micro-partitions/pruning/clustering/warehouse performance as **track-critical high probability**;
- advanced obscure Snowflake internals as lower priority unless the job description or interviewer signals them.
