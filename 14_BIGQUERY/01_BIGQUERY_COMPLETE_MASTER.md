# BigQuery Complete Master Notes

## Role in this curriculum
BigQuery is one of the cloud data-warehouse platforms named in the curriculum. It is supporting knowledge; Snowflake and Fabric remain the specialization priorities.

## Core mental model
BigQuery is a cloud-native analytical data warehouse designed for large-scale SQL analytics without traditional server management.

## Storage/query concepts
Know datasets, tables, views, external tables, partitions and clustering.

## Partitioning
Partitioning divides data into logical partitions, commonly by date/time or integer ranges. A query filtering the partitioning column can reduce scanned data.

## Clustering
Clustering organizes storage based on selected columns to improve query performance for common filters. It is different from partitioning: partitioning creates larger logical segments; clustering organizes data within those segments.

## Cost awareness
A key interview principle: **scan less data**. Select only required columns, filter effectively, use partition filters, and avoid unnecessary repeated full-table processing.

## SQL examples
```sql
SELECT customer_id, SUM(amount) AS total
FROM `project.dataset.orders`
WHERE order_date >= '2026-09-01'
GROUP BY customer_id;
```

## Compare with Snowflake
Be able to say:
“Both are cloud analytical warehouses. I would compare the two using storage/compute model, workload management, pricing, loading, semi-structured support, governance and project requirements rather than claiming one is universally better.”
