# PySpark Complete Master Notes

## Core idea
PySpark is the Python API for Apache Spark. For interview purposes, connect every DataFrame operation to Spark's distributed execution model.

## Read data
```python
from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("demo").getOrCreate()

df = spark.read.option("header", True).option("inferSchema", True).csv("orders.csv")
```
Prefer explicit schemas in production when stability matters.

## Inspect
```python
df.printSchema()
df.show(10, truncate=False)
df.select("customer_id", "amount").show()
```

## Transform
```python
from pyspark.sql import functions as F

clean = (
    df.filter(F.col("amount") > 0)
      .withColumn("order_date", F.to_date("order_date"))
      .dropDuplicates(["order_id"])
)
```

## Aggregation
```python
result = (
    clean.groupBy("customer_id")
         .agg(F.sum("amount").alias("total_amount"),
              F.count("order_id").alias("orders"))
)
```

## Joins
```python
joined = orders.join(customers, "customer_id", "left")
```
Know inner/left/right/full/cross semantics, join keys, duplicate columns and the performance impact of shuffle.

## Window functions
```python
from pyspark.sql.window import Window
w = Window.partitionBy("department").orderBy(F.col("salary").desc())
ranked = df.withColumn("rnk", F.dense_rank().over(w))
```

## JSON / nested data
Know `from_json`, `to_json`, `explode`, `explode_outer`, `struct`, nested column access and schema definitions.

## Null handling
```python
df.na.fill({"amount": 0})
df.na.drop(subset=["order_id"])
```
Use explicit business rules; do not blindly replace every null with zero.

## Deduplication
Use the correct business key. If latest-record semantics are required, use a window and `row_number()` rather than arbitrary `dropDuplicates`.

## Repartition vs coalesce
- `repartition`: reshuffles data to establish a new partition distribution.
- `coalesce`: usually reduces partitions with less movement.
Use them based on the physical problem, not as magic performance switches.

## Broadcast
```python
joined = fact.join(F.broadcast(dim), "product_id", "left")
```
Only when the broadcast side is safely small for executor memory.

## SCD2 pattern
1. Identify business key.
2. Compare tracked attributes.
3. Close existing current version.
4. Insert new version.
5. Maintain effective timestamps/current flag.
6. Make the process idempotent.

## Schema evolution
Define what changes are allowed: additive columns may be easier than type changes/removals. Validate incoming schemas and preserve compatibility with downstream consumers.

## Write formats
For analytics, Parquet/Delta are common columnar table formats. Partitioning should reflect query/data distribution and avoid excessive tiny files.

## Troubleshooting checklist
- Spark UI
- stage/task skew
- shuffle read/write
- spill
- partition sizes
- join strategy
- serialization
- executor memory
- unnecessary actions/collect
- file counts

## Coding problems
- top 3 salaries per department
- latest customer event
- duplicate orders
- running total per customer
- flatten nested JSON
- join fact and dimensions
- count nulls by column
- SCD2 logic
