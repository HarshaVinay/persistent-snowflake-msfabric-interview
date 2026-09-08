# Spark / PySpark — Persistent Reported Questions 2026

## Evidence

Recent Persistent interview reports repeatedly test Spark/PySpark through practical coding and troubleshooting rather than only definitions. citeturn1search0turn1search12

## P0 reported patterns

### RDD vs DataFrame vs Dataset

Be able to explain:
- abstraction level;
- schema/type information;
- optimization;
- typical use cases;
- why DataFrames are commonly preferred for structured analytics.

This is explicitly reported in Persistent interviews. citeturn1search0

### Narrow vs wide transformations

Know that wide transformations require data movement across partitions and can trigger shuffle; narrow transformations can generally be computed from parent partitions without that cross-partition redistribution.

Examples:
- narrow: `map`, `filter`
- wide: `groupByKey`, many joins, `reduceByKey` involves shuffle

Persistent reports explicitly ask this. citeturn1search2turn1search8

### Schema evolution

Question:
> A new field appears in incoming JSON. What do you do?

Discuss:
- schema detection/contract;
- compatibility;
- nullable/default handling;
- versioning;
- downstream impact;
- validation;
- Delta/Lakehouse evolution where appropriate.

This is repeatedly reported. citeturn1search0turn1search2

### Nested JSON

Question:
> How do you parse and flatten nested JSON in PySpark?

Know:
- `from_json`;
- explicit schema;
- `struct` access;
- `explode` for arrays;
- selecting nested fields;
- handling high-cardinality arrays carefully.

Nested JSON flattening is directly reported. citeturn1search2

### Null handling

Recent Persistent interview evidence includes PySpark null checking. citeturn1search12

Be ready with:

```python
df.filter(df.col_name.isNull()).show()
```

and know `dropna`, `fillna`, conditional replacement and why blindly filling every null with zero can corrupt meaning.

### GroupBy

```python
df.groupBy("col_name").count().show()
```

Explain that grouping/aggregation is generally a wide operation and can cause shuffle.

### RDD map

```python
rdd = sc.parallelize([1, 2, 3])
rdd.map(lambda x: x * 2).collect()
```

This was explicitly included in a recent Persistent hands-on report. citeturn1search12

---

## P0 troubleshooting

### Slow Spark job

Answer in this order:
1. inspect Spark UI;
2. identify slow stage;
3. inspect shuffle;
4. inspect partition sizes;
5. check skew;
6. inspect join strategy;
7. reduce data early;
8. consider broadcast for genuinely small data;
9. tune partitions/repartition only with evidence;
10. evaluate cache/persist only if reuse justifies it;
11. compare before/after.

### Executor OOM

Do not immediately say “increase memory.” Discuss:
- skew;
- oversized partitions;
- bad join strategy;
- excessive collect;
- caching too much;
- data explosion from explode;
- serialization;
- partition sizing.

### Data skew

Explain:
- what skew is;
- why one/few keys can dominate;
- how it creates straggler tasks;
- salting or skew-aware strategies;
- broadcast where appropriate;
- AQE/skew handling where available.

Persistent reports include Spark optimization and large-scale scenarios. citeturn1search2turn1search6

---

## P1

- `cache()` vs `persist()`
- `map` vs `flatMap` vs `mapPartitions`
- repartition vs coalesce
- Catalyst optimizer
- AQE
- broadcast joins
- Spark memory
- partitioning strategy
- Parquet
- window functions
- Spark streaming/windowing/watermarking/state

`cache`/`persist`, `map`/`flatMap`/`mapPartitions`, narrow/wide and skew are also reported in Persistent interview material. citeturn1search11

## Coding checklist

Practice from scratch:
1. CSV → clean → Parquet
2. null handling
3. duplicate removal
4. groupBy aggregation
5. window ranking
6. latest record
7. nested JSON flattening
8. fact/dimension join
9. SCD Type 2
10. skew-aware join scenario
