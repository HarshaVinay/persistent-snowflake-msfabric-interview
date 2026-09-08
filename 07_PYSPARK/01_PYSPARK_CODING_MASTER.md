# PySpark Coding Master

## DataFrame basics
```python
from pyspark.sql import functions as F
from pyspark.sql.window import Window

clean = (df
    .filter(F.col("id").isNotNull())
    .dropDuplicates(["id"])
)
```

Know `select`, `filter/where`, `withColumn`, `drop`, `cast`, `when/otherwise`, `groupBy/agg`, joins, `orderBy`, `distinct`, `dropDuplicates`, `explode`, JSON functions and windows.

## Window pattern
```python
w = Window.partitionBy("dept").orderBy(F.col("salary").desc())
result = df.withColumn("rn", F.row_number().over(w)).filter("rn = 1")
```

## Join optimization
Filter/project early. Broadcast only a genuinely small side. Watch for skew and shuffle explosion.

## repartition vs coalesce
`repartition` can increase/decrease partitions and causes a shuffle. `coalesce` normally reduces partitions with less/no full shuffle.

## cache/persist
Use when a dataset is reused and recomputation is material. Choose storage level with `persist`; always validate memory/cost benefits.

## JSON
Use schema + `from_json`, then `explode` arrays and select nested fields. Avoid Python UDFs when built-in Spark functions can express the operation.

## Common coding prompts
- CSV → clean → Parquet.
- Latest record per key.
- Top N per group.
- Flatten nested JSON.
- Join fact/dimension.
- Handle null/duplicates.
- SCD Type 2.
