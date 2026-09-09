# PySpark DataFrame Master Notes

## SparkSession
```python
from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("InterviewPrep").getOrCreate()
```

## Read data
```python
df = spark.read.option("header", True).option("inferSchema", True).csv("orders.csv")
```
For production pipelines, explicit schemas are generally safer than inference.

## Select and filter
```python
df.select("customer_id", "amount")
df.filter(df.amount > 1000)
```

## Derived columns
```python
from pyspark.sql.functions import col, when

df = df.withColumn("segment", when(col("amount") >= 1000, "HIGH").otherwise("LOW"))
```

## Aggregation
```python
from pyspark.sql.functions import sum, count, avg

result = df.groupBy("customer_id").agg(
    sum("amount").alias("total_amount"),
    count("*").alias("orders"),
    avg("amount").alias("avg_amount")
)
```

## Joins
```python
joined = orders.join(customers, on="customer_id", how="left")
```
Before a join, understand the grain and key cardinality.

## Duplicates
```python
df.dropDuplicates(["customer_id", "order_id"])
```
For latest-record logic, use a deterministic window rather than simple deduplication.

## NULL handling
```python
from pyspark.sql.functions import coalesce, lit

df.fillna({"amount": 0})
df = df.withColumn("amount", coalesce(col("amount"), lit(0)))
```
Choose imputation rules from business meaning; don't blindly convert every null to zero.

## JSON
Use `from_json` with an explicit schema for structured parsing, then select nested fields. Use `explode` for arrays.

## Parquet
Parquet is columnar and works well for analytical pipelines. Read only required columns and preserve a useful schema.

## Window example
```python
from pyspark.sql.window import Window
from pyspark.sql.functions import row_number

w = Window.partitionBy("customer_id").orderBy(col("updated_at").desc())
latest = df.withColumn("rn", row_number().over(w)).filter(col("rn") == 1)
```

## UDF rule
Prefer built-in Spark functions when possible because they expose more information to Spark's optimizer and avoid unnecessary Python-level execution overhead.

## Interview checklist
Be able to explain every transformation, whether it is narrow/wide, whether it triggers shuffle, expected partition behavior, and how you would test the result.
