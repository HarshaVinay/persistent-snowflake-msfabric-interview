# Apache Spark Master Notes — Persistent Snowflake_MSFabric

## Curriculum coverage
Spark ecosystem, introduction/setup, Hadoop vs Spark, local/cluster mode, actions, RDDs, key-value RDDs, loading/saving, shared variables, transformations/actions, cluster managers, `spark-submit`, caching, memory tuning, job troubleshooting, DataFrames, Datasets, aggregations, SparkSession, JSON/Parquet, complex transformations, advanced APIs, windows, real-time processing, Spark engine, Azure Event Hubs, windowing, watermarking, state management and streaming best practices.

## What is Spark?
Spark is a distributed processing engine that divides data/computation across a cluster and executes work in parallel. It supports batch, SQL, streaming and multiple languages.

## Ecosystem
```text
Spark Core      → execution, RDDs, scheduling
Spark SQL       → DataFrames, SQL
Structured Streaming → continuous data
MLlib           → machine learning
GraphX          → graph processing
```

## Architecture
```text
Driver
  ↓
Cluster Manager
  ↓
Executors on Worker Nodes
  ↓
Tasks operate on Partitions
```

Driver plans and coordinates. Executors execute tasks and keep/cache data. Cluster manager allocates resources.

## Execution hierarchy
```text
Application → Job → Stage → Task → Partition
```
An action triggers execution. Shuffle boundaries commonly divide stages.

## Lazy evaluation
Transformations build a logical plan; Spark delays execution until an action is called. This allows optimization and avoids unnecessary work.

## Transformations vs actions
Transformations: `map`, `filter`, `select`, `groupBy`, `join` (many are lazy).
Actions: `count`, `collect`, `show`, `write`, `save`.

## Narrow vs wide
Narrow: each output partition depends on a small number of input partitions; typically no full shuffle.
Wide: output depends on multiple input partitions and generally requires shuffle. Examples: `groupBy`, many joins, `orderBy`.

## RDD vs DataFrame vs Dataset
RDD = low-level distributed object collection.
DataFrame = structured, schema-aware tabular abstraction optimized by Spark SQL.
Dataset = typed API mainly associated with JVM/Scala/Java.
For most structured ETL, prefer DataFrames unless lower-level control is needed.

## Partitioning
Partitions are parallelism units. Too few can underuse the cluster; too many can increase scheduling/file overhead. Inspect data size and workload rather than using a magic number.

## `repartition()` vs `coalesce()`
`repartition(n)` can increase/decrease partitions and normally triggers shuffle.
`coalesce(n)` reduces partitions with less movement and is useful after filtering, but cannot increase partition count.

## Cache/persist
Cache/persist when the same computed dataset is reused. Do not cache everything; it consumes memory/storage resources and can hurt performance.

## Broadcast join
Broadcast a genuinely small dataset so Spark can avoid shuffling the large side for suitable joins.

## Data skew
Skew occurs when a few keys own disproportionate data, causing straggler tasks. Approaches include filtering, salting, better partitioning, broadcast joins where appropriate, and AQE skew handling.

## Catalyst and AQE
Catalyst optimizes Spark SQL logical/physical plans. Adaptive Query Execution can adapt execution based on runtime statistics, including certain join/partition/skew decisions.

## Troubleshooting workflow
1. Spark UI.
2. Find slow stage.
3. Check shuffle read/write and task duration.
4. Check partition-size imbalance.
5. Inspect join plan.
6. Check skew.
7. Reduce scanned data and columns.
8. Choose a justified join/partition strategy.
9. Re-run and compare.

## Streaming
```text
Source → readStream → transformations → window/aggregation → writeStream → sink
```
Know Event Hubs, checkpoints, watermarking, state and recovery at curriculum level.

## Interview answer
"Spark distributes data into partitions and executes tasks across executors. Transformations are lazy, while actions trigger jobs. Wide transformations create shuffle boundaries, which can become performance bottlenecks. For structured ETL I usually prefer DataFrames and tune joins, partitions, skew and caching based on Spark UI evidence."

## Priority
P0.
