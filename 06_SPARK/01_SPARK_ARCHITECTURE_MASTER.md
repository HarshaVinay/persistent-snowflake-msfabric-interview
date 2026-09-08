# Apache Spark Architecture Master

## Mental model
Driver creates the application plan and coordinates execution. Spark breaks work into jobs → stages → tasks. Tasks operate on partitions and run on executors. A cluster manager allocates cluster resources.

## Know these cold
Driver, executor, cluster manager, SparkSession, application, job, stage, task, partition, DAG, shuffle, lineage, lazy evaluation, transformation, action.

## Narrow vs wide
Narrow: each output partition depends on a small/local set of input partitions; usually no shuffle. Examples include `map` and many `filter` operations.
Wide: output depends on data from multiple input partitions and normally needs shuffle. Examples include `groupByKey`, many aggregations and joins.

## Lazy evaluation
Transformations build a plan; an action triggers execution. This lets Spark optimize the plan before running it.

## Fault tolerance
RDD lineage lets Spark recompute lost partitions. For production, checkpoints can truncate long lineage/state when required.

## Local vs cluster
Local mode is development/testing. Cluster mode distributes work over worker resources.

## Common interview questions
1. Explain Spark architecture.
2. Job vs stage vs task.
3. Why does shuffle create stages?
4. Lazy vs eager evaluation.
5. Narrow vs wide transformation.
6. What is a partition?
7. What happens when an executor fails?
