# Data Engineering Scenario Master

## Universal answer framework
Always answer in this order:
**requirements → source/grain → volume/latency → ingestion → storage → transformation → serving → data quality → security → recovery → monitoring → cost/performance.**

## Scenario 1 — Spark job is slow
1. Inspect Spark UI.
2. Identify the slow stage/task.
3. Check shuffle read/write, spill and skew.
4. Check partition sizes.
5. Inspect physical join strategy.
6. Filter/project early.
7. Broadcast only a genuinely small side.
8. Consider repartitioning/AQE when justified.
9. Cache only reused data.
10. Benchmark before/after.

## Scenario 2 — Data skew
Confirm key-frequency distribution. If one/few keys dominate, consider salting, pre-aggregation, skew-aware join handling/AQE and better partitioning. Never assume adding executors fixes skew.

## Scenario 3 — Executor OOM
Determine whether the cause is oversized partitions, a too-large broadcast, skew, row explosion from joins, excessive caching, or driver-side collection. Fix the cause before blindly increasing memory.

## Scenario 4 — Small files
Find whether too many partitions, frequent micro-batches or tiny source files create the problem. Reduce unnecessary output fragmentation, compact where supported, and choose partitioning based on query/data distribution.

## Scenario 5 — Schema evolution
Separate additive compatible changes from breaking type/removal changes. Validate incoming schema, quarantine incompatible records, update contracts and test downstream models.

## Scenario 6 — Duplicate data
Define the business key. Stage raw input. Apply deterministic deduplication, usually keeping the appropriate latest event. Use idempotent `MERGE`/upsert semantics where applicable. Validate row counts and duplicate rates.

## Scenario 7 — Pipeline failure
Capture error and run metadata. Retry transient failures. Isolate bad input. Resume from a safe checkpoint/watermark when supported. Ensure reruns cannot duplicate data. Alert the correct owner.

## Scenario 8 — Slow Snowflake query
Use Query Profile. Check bytes scanned/pruning, joins, aggregation, spilling/queueing and warehouse behavior. Improve SQL/filtering. Consider clustering only when the workload justifies it. Compare elapsed time and credits/cost.

## Scenario 9 — PII
Classify sensitive data, minimize access, use least privilege/RBAC, masking and row-level controls where appropriate, secure authentication, encryption and audit/monitoring. Explain platform-specific enforcement rather than using generic security buzzwords.

## Scenario 10 — 10 TB pipeline
Use cloud/object storage, distributed processing, columnar formats, incremental/CDC ingestion, scalable orchestration and monitoring. Design for retries, idempotency and partition-aware processing. Choose Snowflake/Fabric based on workload and serving requirements.

## Scenario 11 — Disaster project at production scale
```text
Source CSV/API
   ↓
Landing object storage
   ↓
Bronze
   ↓
PySpark cleaning
   ↓
Silver
   ↓
Dimensional Gold
   ↓
Snowflake/Fabric Warehouse
   ↓
Power BI
```
Add quality gates, incremental loads, audit columns, security and monitoring.

## Scenario 12 — Cricket project at production scale
```text
Landing files / stream
        ↓
Airflow / Fabric Data Factory
        ↓
Bronze
        ↓
PySpark / SQL
        ↓
Silver
        ↓
dbt / SQL models
        ↓
Gold
        ↓
Snowflake / Fabric Warehouse / Semantic Model
        ↓
BI / application
```

## Scenario 13 — Interviewer changes requirements
Do not defend the original design blindly. Restate the changed requirement, identify which architectural component changes, explain the trade-off, and preserve data quality/security/recovery guarantees.
