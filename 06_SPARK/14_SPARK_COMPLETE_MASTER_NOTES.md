# Apache Spark Complete Master Notes

## What is Spark?
Spark is a distributed data-processing engine. It splits data/work into partitions and schedules parallel computation across executors.

## Ecosystem
- Spark Core: execution, RDDs, scheduling and fault tolerance.
- Spark SQL: DataFrames, Datasets and SQL.
- Structured Streaming: continuous data processing.
- MLlib: machine learning.
- GraphX: graph processing.

## Hadoop vs Spark
Spark is a compute engine, not a storage system. It can use HDFS, cloud object storage and other sources. Hadoop MapReduce is an older batch processing model; Spark provides a DAG-based unified engine and APIs for SQL, DataFrames and streaming.

## Architecture
`Driver → Cluster Manager → Executors on worker nodes → Tasks over partitions → results`.

Driver responsibilities: build/coordinate the application, schedule tasks and maintain application state.
Executor responsibilities: execute tasks and cache data.
Cluster manager: allocates resources.

## Execution hierarchy
`Application → Job → Stage → Task`.
An action triggers execution. Shuffle boundaries often create stage boundaries.

## Lazy evaluation
Transformations create a logical lineage/plan; Spark delays execution until an action requires a result. This allows optimization and avoids unnecessary work.

## Transformations vs actions
Transformations: `map`, `filter`, `select`, `join`, `groupBy`.
Actions: `count`, `collect`, `show`, writes and other result-producing operations.

## Narrow vs wide
Narrow: each output partition depends on a limited number of input partitions; generally no full-data shuffle. Examples: `filter`, `map`.
Wide: output can depend on many input partitions; shuffle may be required. Examples: `groupBy`, many joins, `distinct`.

## Partitions and shuffle
A partition is a unit of parallel data processing. Shuffle redistributes data across executors, often adding network, disk and serialization costs.

## RDD
Immutable distributed collection with low-level transformation/action APIs. Useful when fine-grained control is required, but DataFrames are generally preferred for structured data.

## DataFrame / Dataset
DataFrame: distributed structured data with schema and optimizer support.
Dataset: typed API in languages that support it, notably Scala/Java. PySpark users primarily work with DataFrames.

## SparkSession
Main entry point for modern Spark SQL/DataFrame applications.

## Partition control
`repartition()` can increase/decrease partitions and generally performs a shuffle. `coalesce()` is commonly used to reduce partitions with less shuffle.

## Cache / persist
Cache keeps reused data available for faster subsequent operations when beneficial. `persist` allows explicit storage levels. Caching too much wastes memory.

## Broadcast join
If one side is sufficiently small, broadcast it so executors avoid a large shuffle of that side. Do not broadcast data that is too large for executor memory.

## Data skew
One/few keys receive disproportionately large data, creating straggler tasks. Remedies can include salting, pre-aggregation, different join strategy, skew-aware methods/AQE and better partitioning.

## Catalyst and AQE
Catalyst is Spark SQL's query optimizer. Adaptive Query Execution can adjust parts of the physical plan at runtime based on observed statistics.

## Memory troubleshooting
When a task or executor fails, inspect Spark UI, stage metrics, task sizes, shuffle, spill and skew. Do not treat “increase memory” as the first or only solution.

## Streaming
Structured Streaming uses the DataFrame/Dataset model for continuous data. Know checkpoints, output modes, event time, windows, watermarks and state.

## Interview answer: slow Spark job
“I first inspect the Spark UI to identify the slow stage and look for large shuffles, skew, spill and uneven partition sizes. Then I review the physical plan and join strategy, filter/project early, use broadcast only for genuinely small dimensions, tune partitions, consider AQE and cache only reused data. Finally I rerun and compare runtime and resource usage.”

## Persistent focus
Reported Persistent interviews repeatedly probe narrow/wide transformations, skew, partitioning, schema evolution, SCD2, nested JSON, repartition/coalesce and performance troubleshooting.
