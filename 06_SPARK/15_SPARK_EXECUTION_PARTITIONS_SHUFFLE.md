# Spark Execution, Partitions & Shuffle

## Execution hierarchy
```text
Application
   ↓
Driver
   ↓
Job
   ↓
Stages
   ↓
Tasks
   ↓
Executor cores
```

A job is created by an action. Spark breaks work into stages around shuffle boundaries and then runs tasks over partitions.

## Partition
A partition is a logical chunk of distributed data. Tasks generally process one partition at a time.

More partitions can improve parallelism, but too many can create scheduling and I/O overhead. Too few can underutilize executors and create oversized tasks.

## Lazy evaluation
Transformations build a logical lineage/plan. Execution begins when an action requires a result.

## Narrow transformation
Each output partition depends on a limited set of input partitions.
Examples: `map`, `filter`, `select`-style operations.
Usually no full data redistribution is required.

## Wide transformation
An output partition depends on many input partitions and typically requires shuffle.
Examples: `groupByKey`, many joins, `reduceByKey`, `orderBy`.

## Shuffle
Shuffle redistributes data across executors, often involving network, disk and serialization. It is a common performance hotspot.

## Repartition vs coalesce
- `repartition(n)` can increase or decrease partitions and generally causes a shuffle.
- `coalesce(n)` is primarily used to reduce partitions with less movement, so it is useful when reducing output file count.

## Spark UI troubleshooting
Inspect:
- stages with long duration;
- task duration spread;
- shuffle read/write;
- input/output size;
- spill;
- executor failures;
- skewed partitions.

## Data skew
If a few keys contain a disproportionate amount of data, some partitions become much larger than others. The cluster waits for straggler tasks.

Potential techniques:
- filter early;
- broadcast a genuinely small dimension;
- repartition appropriately;
- salting for severe key skew;
- Spark's adaptive/skew handling where supported.

## Interview rule
Do not say “increase the number of partitions” automatically. First inspect actual partition sizes and the stage bottleneck.
