# Snowflake Micro-Partitions, Pruning & Clustering

## Micro-partitions
Snowflake automatically divides table data into contiguous micro-partitions. Current Snowflake documentation describes 50–500 MB of uncompressed data per micro-partition; the stored representation is compressed and columnar. Snowflake maintains metadata such as column value ranges and distinct-value information.

Source: https://docs.snowflake.com/en/user-guide/tables-clustering-micropartitions

## Why they matter
Micro-partitions enable fine-grained pruning and columnar scanning. A selective predicate can allow Snowflake to skip partitions that cannot contain matching rows.

## Pruning
Conceptually:
```text
Filter predicate
   ↓
Micro-partition metadata
   ↓
Can this partition contain a match?
   ├── No → skip
   └── Yes → scan relevant data
```

Less data scanned generally means less I/O and lower execution work.

## Clustering
Data naturally acquires an ordering based on load/insert patterns. A clustering key can be defined when very large tables have important repeated access patterns and natural clustering no longer provides adequate pruning.

## Clustering is not partitioning
Snowflake already micro-partitions tables automatically. A clustering key is an additional organization strategy used for selected tables/workloads.

## When to consider clustering
- large table;
- frequent selective filters on chosen columns;
- poor natural clustering/overlap;
- measurable performance problem;
- benefit justifies credit/storage maintenance cost.

## Why not cluster everything?
Reclustering consumes compute and can create additional storage turnover. Current Snowflake documentation explicitly advises considering credit and storage cost before defining a clustering key.

Source: https://docs.snowflake.com/en/user-guide/tables-clustering-keys

## Interview trap
Bad answer: “Add a clustering key whenever a table is slow.”

Better answer: “First inspect the query profile and pruning behavior. If a very large table repeatedly filters on a column and natural clustering is poor, I would evaluate clustering and measure the performance benefit against ongoing cost.”
