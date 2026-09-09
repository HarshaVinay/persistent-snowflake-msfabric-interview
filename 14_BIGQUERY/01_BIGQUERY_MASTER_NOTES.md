# BigQuery Master Notes

## Scope
BigQuery appears in the user's curriculum as a cloud data warehouse platform. It is supporting knowledge, not the specialization center.

## Core mental model
Serverless analytics warehouse: storage and query execution are managed by the platform; users focus on datasets/tables, SQL and workload design.

## Know
- datasets
- native vs external tables
- partitioning
- clustering
- partition pruning
- query cost awareness
- materialized views
- semi-structured data basics

## Partitioning
Partition tables on a column that aligns with common filters, such as date, so queries can scan less data.

## Clustering
Organizes data to improve pruning/scan efficiency for common access patterns within partitions/tables.

## Interview contrasts
BigQuery vs traditional RDBMS; partitioning vs clustering; native vs external table; warehouse vs lake.

## Priority
P1/P2 for this specific Persistent Snowflake_MSFabric role unless the project/interviewer introduces BigQuery directly.
