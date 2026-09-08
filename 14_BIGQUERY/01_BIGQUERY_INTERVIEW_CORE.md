# BigQuery Interview Core

## Know
Dataset, table, partitioning, clustering, partition pruning, `_PARTITIONDATE`, `_PARTITIONTIME`, query cost, external tables and materialized views.

## Key distinction
Partitioning groups data by a partitioning column/time boundary; clustering organizes data within storage blocks to improve pruning for common predicates. Use both only when workload justifies them.

## Interview prompts
- Why partition a table?
- Partitioning vs clustering?
- How do you reduce BigQuery query cost?
- What is partition pruning?

## Track priority
Curriculum support topic. Do not let BigQuery displace Snowflake/Fabric because those are the assigned specialization.