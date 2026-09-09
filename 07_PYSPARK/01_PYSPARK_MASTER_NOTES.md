# PySpark Master Notes — Persistent Snowflake_MSFabric

## Core
PySpark is Spark's Python API. Use it to perform distributed transformations with DataFrames, SQL, RDDs and Structured Streaming.

## Standard DataFrame flow
```python
from pyspark.sql import SparkSession, functions as F, Window
spark = SparkSession.builder.appName("InterviewPrep").getOrCreate()
df = spark.read.option("header", True).csv("orders.csv")
df = df.withColumn("amount", F.col("amount").cast("double"))
```

## Essential operations
`select`, `withColumn`, `filter/where`, `drop`, `distinct`, `dropDuplicates`, `groupBy`, `agg`, `join`, `orderBy`, `when`, `coalesce`, `na.fill`, `na.drop`, `explode`, `collect_list`, window functions.

## Joins
Know inner, left, right, full, cross and self joins. Always consider join keys, data volume, nulls, duplicates and skew.

## Nested JSON
Use explicit schemas when practical, then `explode` arrays and select nested fields. Avoid indiscriminate `collect()` because it moves data to the driver.

## Windows
```python
w = Window.partitionBy("department").orderBy(F.col("salary").desc())
df.withColumn("rn", F.row_number().over(w))
```
Use for ranking, latest-record selection, running totals, lag/lead and top-N-per-group.

## Null handling
Use `isNull`, `isNotNull`, `na.fill`, `when` and explicit business rules. Do not silently replace every missing value with zero without understanding the domain.

## Deduplication
For simple duplicates: `dropDuplicates(keys)`.
For latest-record logic, use a window with deterministic ordering and keep `row_number() = 1`.

## Performance
- Filter/project early.
- Avoid Python UDFs where built-ins work.
- Broadcast genuinely small dimensions.
- Tune partitions.
- Handle skew.
- Avoid huge `collect()`.
- Use cache only when reuse justifies it.
- Check Spark UI and execution plan.

## Interview coding set
1. CSV → cleaned DataFrame → Parquet.
2. Top 3 salaries per department.
3. Latest customer record.
4. Flatten nested JSON.
5. Join fact/dimension.
6. SCD2 logic.
7. Find duplicate keys.
8. Running total.

## Persistent evidence
Recent reports mention DataFrame creation, Python/PySpark coding, nested JSON flattening, null handling, groupBy, RDD operations, narrow/wide, skew, schema evolution, SCD2 and optimization.
