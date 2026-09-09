# Snowflake Master Notes — Persistent Snowflake_MSFabric

## Curriculum coverage
Introduction/setup, architecture, virtual warehouses, micro-partitions, physical storage, storage-level clustering, bulk loading, CSV/JSON/Parquet/Avro/ORC, stages/error handling, performance, tables/views, compression, pruning, statistics, auto-scaling/multi-cluster, workload/resource monitoring, cost, execution plans/profiling, cache layers, semi-structured data, replication/failover, disaster recovery, retention, SQL/JavaScript/Python UDFs, data sharing, stored procedures, Snowpark, DataFrames, external libraries, dbt integration, Python connector, REST API, authentication, access control, RBAC, masking, RLS and audit/monitoring.

## Architecture
Snowflake separates storage and compute. Virtual warehouses provide compute; cloud services coordinate metadata, authentication, optimization and other platform functions.

## Virtual warehouses
A warehouse is a compute cluster used for SQL/DML/loading work. Scaling up generally provides more compute per cluster. Multi-cluster warehouses address concurrency by adding clusters within limits/configuration.

Know: size, auto-suspend, auto-resume, workload isolation, concurrency, cost trade-offs.

## Micro-partitions
Snowflake automatically divides table data into micro-partitions. Current Snowflake documentation describes them as contiguous, columnar storage units and says Snowflake maintains metadata such as value ranges and distinct-value information. Micro-partitioning is automatic. citeturn141865search0

## Pruning
Pruning uses micro-partition metadata to avoid scanning partitions that cannot satisfy a predicate. Better data organization can improve pruning. citeturn141865search0

## Clustering
Clustering organizes/maintains data so relevant ranges are more closely grouped for common query patterns. Use a clustering key only when the large-table workload justifies maintenance cost. Clustering depth is a diagnostic signal, but actual query performance remains the business outcome. citeturn141865search0

## Loading flow
```text
Cloud files
   ↓
Stage
   ↓
COPY INTO
   ↓
Table
   ↓
Micro-partitions
```

Know user/table/named/internal/external stages, file formats, validation/error handling and `COPY INTO`.

## Practical loading pattern
```sql
CREATE FILE FORMAT my_csv TYPE = CSV SKIP_HEADER = 1;
CREATE STAGE my_stage FILE_FORMAT = my_csv;
COPY INTO target_table FROM @my_stage;
```
Exact syntax/options should be checked against the target account/version when using advanced options.

## `MERGE`
Use `MERGE` for matched/unmatched change application, especially incremental pipelines and SCD2 patterns.

## `QUALIFY`
Filters results after window functions without requiring an extra subquery in Snowflake.

```sql
SELECT *, ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY updated_at DESC) rn
FROM customer_changes
QUALIFY rn = 1;
```

## Semi-structured
`VARIANT` can hold JSON-like data. Learn path extraction and `FLATTEN` for arrays/nested structures.

## Table types
- Permanent: long-lived business data; supports recovery features such as Time Travel and Fail-safe under applicable retention.
- Temporary: session-scoped.
- Transient: persistent but without Fail-safe; useful for recreatable/intermediate data.

## View vs materialized view
View stores query definition. Materialized view maintains a stored result for supported workloads and adds maintenance/storage cost.

## Time Travel, Fail-safe, cloning
Time Travel = historical access/recovery within configured retention.
Fail-safe = Snowflake-managed recovery period after Time Travel.
Zero-copy cloning = creates an independent logical copy while initially sharing underlying storage structures; changes require additional storage. Cloning can also be combined with Time Travel. citeturn141865search9

## Performance workflow
```text
Slow query
 ↓
Query Profile / execution details
 ↓
Scan / join / spill / queue bottleneck
 ↓
Pruning + SQL + join strategy + clustering if justified
 ↓
Warehouse/concurrency check
 ↓
Cache check
 ↓
Measure again
```

Do not blindly increase warehouse size before identifying the bottleneck.

## Caching
Know result cache, metadata-related caching and warehouse/local-data caching at conceptual level; always explain when reuse and cache eligibility matter.

## Replication/DR
Know cross-region replication, failover/failback concepts, RPO/RTO thinking, recovery testing and retention.

## UDFs/procedures/Snowpark
Use UDFs for reusable custom logic; stored procedures for procedural workflows/business logic; Snowpark for pushing Python/Scala/Java transformations close to Snowflake data without extracting large datasets unnecessarily.

## Security
RBAC = roles + privileges.
Masking policies protect sensitive values.
Row access policies restrict visible rows.
Audit/monitoring provides accountability.

## dbt integration
Know models, materializations, sources/seeds, tests, incremental models, snapshots and Snowflake deployment.

## Persistent relevance
Direct report: zero-copy cloning. Recent reports/current roles also reinforce Snowflake, SQL, PySpark, ingestion, performance and pipeline topics.

## P0 checklist
[ ] architecture
[ ] warehouse
[ ] stages
[ ] COPY
[ ] file formats
[ ] micro-partitions
[ ] pruning
[ ] clustering
[ ] performance
[ ] VARIANT/FLATTEN
[ ] MERGE
[ ] QUALIFY
[ ] Streams/CDC
[ ] Time Travel
[ ] Fail-safe
[ ] cloning
[ ] RBAC/masking/RLS
[ ] Snowpark
[ ] dbt
