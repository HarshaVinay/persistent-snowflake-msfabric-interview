# Persistent Spark / PySpark — Scenario Priority

## P0 questions

### 1. Narrow vs wide transformation
**Expected:** Narrow transformations do not require data movement across partitions; wide transformations require redistribution/shuffle.

**Examples:** `map`, `filter` are commonly narrow; `groupByKey`, many joins and aggregations can be wide.

### 2. Data skew
Explain:
- what skew is
- why one/few partitions become stragglers
- how to detect it
- salting
- broadcast join when a side is small enough
- repartitioning when appropriate
- AQE/skew handling where supported

### 3. Slow Spark job
Use a troubleshooting sequence:
1. inspect Spark UI
2. identify slow stage
3. inspect shuffle
4. inspect partition sizes
5. check skew
6. inspect join strategy
7. filter/project early
8. consider broadcast
9. tune partitions
10. validate runtime and cost

### 4. Small-file problem
Explain why many tiny files create metadata/listing/opening overhead and inefficient reads. Discuss compaction/repartitioning and platform-specific optimization rather than blindly increasing compute.

### 5. Schema evolution
Scenario: incoming JSON gets a new column.
Answer should cover:
- compatibility assessment
- schema inference vs explicit schema
- nullable/new field handling
- controlled evolution
- downstream impact
- data-quality validation
- rollback/replay strategy

### 6. SCD Type 2
Explain:
- business key
- surrogate key where appropriate
- effective start/end dates
- current flag
- change detection
- expire old version
- insert new version
- idempotency

### 7. Repartition vs coalesce
Know when a full shuffle is justified and when reducing partitions can avoid an unnecessary shuffle.

### 8. Cache vs persist
Know that caching is a persistence strategy and that `persist` allows an explicit storage level. Explain that neither should be used automatically; materialize only when reuse justifies memory/storage cost.

## P1
- RDD vs DataFrame vs Dataset
- lazy evaluation
- DAG/job/stage/task
- SparkSession
- broadcast join
- Catalyst
- AQE
- JSON/Parquet
- window functions
- executor memory

## Evidence
Recent Persistent reports repeatedly include narrow/wide transformations, schema evolution, SCD2, skew, repartitioning and Spark optimization. These reports include experienced candidates, so use them as interview-pattern evidence rather than guarantees of fresher depth.
