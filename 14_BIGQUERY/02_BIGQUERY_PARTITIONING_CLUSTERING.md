# BigQuery Partitioning, Clustering & Cost

## Why partitioning?
Partitioning splits a table into logical storage partitions, commonly by ingestion/date/timestamp or an integer range. Queries that filter on the partitioning column can scan less data.

## Why clustering?
Clustering organizes data within partitions around selected columns to improve pruning for common filters.

## Partition pruning
```text
Query filter
   ↓
Partition elimination
   ↓
Read fewer partitions
   ↓
Lower bytes processed / better performance
```

## Interview comparison
Partitioning is usually the first large-scale pruning dimension; clustering refines organization inside partitions. The exact mechanics and billing behavior are platform-specific.

## Good design
Choose partition keys aligned with real query patterns. Avoid unnecessary high-cardinality partitioning or a partition key that users rarely filter.

## Current project connection
If cricket analytics were stored in BigQuery, date-based partitioning on match/event dates could support common time-window queries, with clustering on frequent dimensions such as team or venue if justified by workload evidence.
