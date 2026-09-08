# P0 Interview Core

## Objective
Prepare for the Persistent Snowflake_MSFabric client interview using the user's exact curriculum plus verified/reported Persistent interview patterns.

## Core sequence

### 1. SQL
Must solve without help:
- second/third highest salary
- top N per group
- employee vs manager
- duplicate detection/removal
- latest record per key
- `ROW_NUMBER`, `RANK`, `DENSE_RANK`
- running totals
- moving averages
- joins
- CTE/subqueries
- NULL handling
- conditional aggregation

### 2. Python
Must be comfortable coding:
- lists/tuples/sets/dicts
- loops/functions
- lambda/comprehensions
- duplicate removal without relying on `set` when constraints forbid it
- second-highest value
- exception handling
- JSON/file handling
- OOP basics
- Pandas transformations

### 3. PySpark/Spark
Must explain and demonstrate:
- driver/executor/cluster manager
- job/stage/task
- lazy evaluation
- transformations/actions
- narrow/wide transformations
- shuffle
- RDD/DataFrame/Dataset
- joins and broadcast
- partitioning
- repartition/coalesce
- cache/persist
- data skew
- schema evolution
- JSON flattening
- Spark optimization

### 4. Snowflake
Must explain with examples:
- architecture
- storage/compute separation
- virtual warehouses
- micro-partitions
- pruning
- clustering
- stages
- file formats
- COPY INTO
- MERGE
- QUALIFY
- VARIANT/FLATTEN
- Streams/CDC
- Time Travel
- Fail-safe
- zero-copy cloning
- performance/cost optimization
- RBAC/masking/RLS
- Snowpark

### 5. Data engineering
Must be able to design:
- ETL/ELT
- full/incremental loads
- idempotent pipelines
- SCD2
- data-quality checks
- schema evolution
- data lake/warehouse/lakehouse
- star schema
- fact/dimension model

### 6. Fabric
For this specific curriculum, know:
- OneLake
- Lakehouse
- Warehouse
- Delta
- Spark/PySpark
- Bronze/Silver/Gold
- Data Factory
- Copy Activity
- Dataflows Gen2
- incremental ingestion
- SQL endpoint/T-SQL
- Power BI integration
- RLS/CLS
- lineage/monitoring
- CI/CD

## Scenario answer framework
**Clarify → identify grain/volume/SLA → architecture → ingestion → transformation → storage/serving → quality → security → failure recovery → monitoring → cost/performance.**

## Evidence status
The SQL/Python/PySpark/Snowflake items above have strong support from recent Persistent interview reports. Fabric-specific items are primarily curriculum-driven because public Persistent reports are much less explicit about Fabric. citeturn0search0turn0search2turn0search5
