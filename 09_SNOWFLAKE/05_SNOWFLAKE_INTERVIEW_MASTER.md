# Snowflake Interview Master

## Architecture
Separate storage, compute and cloud services. Compute is supplied by virtual warehouses; storage is managed by Snowflake.

## Micro-partitions
Snowflake automatically partitions table data into contiguous micro-partitions and stores metadata such as column value ranges. Metadata enables pruning. citeturn969057search1

## Clustering
Natural ordering can affect pruning. Explicit clustering keys can be used when large-table access patterns justify the maintenance cost.

## Loading
Know: stage → file format → `COPY INTO` → validation/error handling. Distinguish internal and external stages.

## SQL patterns
`QUALIFY` filters results after window functions without requiring an extra subquery in supported Snowflake SQL patterns. `MERGE` supports matched/unmatched conditional DML and is central to upsert/incremental pipelines.

## Streams / CDC
A stream records change information for supported source objects so downstream processing can consume changes. Tasks can schedule/orchestrate SQL work.

## Semi-structured
Know `VARIANT`, JSON path access and `FLATTEN`.

## History/recovery
Time Travel provides historical access within configured retention. Fail-safe is separate from Time Travel. Zero-copy cloning creates a logical clone without immediately copying all underlying micro-partition data.

## Performance
Start with Query Profile. Ask: what is scanning, what is spilling, are partitions being pruned, is warehouse compute/queueing the bottleneck, and is the query scanning unnecessary columns/rows?

## Security
RBAC, roles/privileges, masking policies, row access policies and auditing/monitoring.

## Snowpark
Lets developers express processing in supported languages such as Python while pushing work toward Snowflake execution rather than moving data unnecessarily.

## Current reported interview signal
Persistent reports include zero-copy cloning and Snowflake hands-on topics alongside SQL and PySpark. Treat vendor-specific details as track-focused preparation unless the question is directly reported. citeturn567821search3