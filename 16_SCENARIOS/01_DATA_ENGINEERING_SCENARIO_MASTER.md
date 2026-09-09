# Data Engineering Scenario Master Notes

## Scenario framework
Always answer:
**Requirements → source/grain → volume/latency → ingestion → storage → transformation → serving → quality → security → recovery → monitoring → cost.**

## Slow Spark job
Inspect Spark UI → identify slow stage → shuffle → skew → partitions → join strategy → column pruning/filtering → AQE/cache only when justified → benchmark again.

## Skewed join
Confirm skewed keys. Filter/project early; broadcast a genuinely small side; salt only where appropriate; consider AQE/skew handling; verify partition balance.

## Executor OOM
Find whether driver/executor is collecting too much data, skew is causing oversized partitions, joins are exploding rows, or caching is consuming memory. Fix root cause before blindly increasing memory.

## Small files
Identify cause: excessive partitions/output commits/micro-batches. Compact/optimize with platform-supported mechanisms; choose sensible file sizes and partitioning. Avoid over-partitioning.

## Schema evolution
Detect new fields/type changes, distinguish additive from breaking changes, update schema contracts deliberately, quarantine incompatible records and test downstream impact.

## Duplicate data
Use business key + deterministic latest-record logic; enforce idempotent writes with MERGE/upsert where appropriate.

## Failed pipeline
Use retries, checkpoints/watermarks, idempotency, logging, alerts, quarantine and restart from the last safe point when architecture permits.

## Slow Snowflake query
Query Profile → scan/joins/queue/spill → pruning → SQL → clustering if justified → warehouse/concurrency → cache → measure cost and elapsed time.

## PII
Least privilege + RBAC + masking/row access policies + secure authentication + audit/monitoring. Explain exactly where security is evaluated in the platform being used.

## End-to-end architecture
```text
Sources
 ↓
Landing/Raw
 ↓
Bronze
 ↓
Silver
 ↓
Gold
 ↓
Warehouse/Semantic layer
 ↓
BI
```
Add orchestration, data quality, security, observability, retries and incremental/CDC processing.
