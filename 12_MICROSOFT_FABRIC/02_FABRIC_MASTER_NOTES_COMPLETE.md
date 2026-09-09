# Microsoft Fabric Master Notes — Persistent Snowflake_MSFabric

## Curriculum coverage
Fabric introduction, evolution from Synapse/Power BI, workloads, Data Engineering, Data Factory, Data Science, Warehouse, Real-Time Analytics, SaaS model, Lakehouse/Warehouse/Datamart, workspace, OneLake, Lakehouse, files/Delta, Spark/PySpark, Medallion, pipelines, Copy Activity/Dataflows Gen2, parameterization/scheduling, Warehouse/SQL endpoint/T-SQL, performance, star schema, Power BI, streaming, governance, RLS/CLS, lineage, monitoring and CI/CD.

## Fabric mental model
```text
                    Microsoft Fabric
                           |
        +------------------+------------------+
        |                  |                  |
   Data Engineering   Data Factory       Data Warehouse
        |                  |                  |
      Spark             Pipelines          T-SQL
        +------------------+------------------+
                           |
                         OneLake
                           |
                    Power BI / Analytics
```

Microsoft documents OneLake as Fabric's single, unified, logical data lake for the organization. citeturn141865search1

## OneLake
OneLake is provisioned with Fabric and is the common data foundation. A Fabric Lakehouse exposes Files and Tables areas. Data can be ingested through upload, pipelines/dataflows/streaming, or external shortcuts/mirroring. citeturn141865search2turn141865search3

## Lakehouse
A Fabric Lakehouse combines lake-style file/data flexibility with queryable tables and Spark/SQL access. Current Microsoft documentation describes Delta-backed tables, Spark for engineering and SQL for analytics, with Power BI/pipeline/dataflow integration. citeturn141865search4

## Warehouse
Warehouse is SQL/T-SQL oriented for structured analytical workloads. Know facts, dimensions, star schema, loading and query optimization.

## Lakehouse vs Warehouse
```text
Lakehouse → Spark/Python/Scala/SQL, structured + unstructured, engineering-first
Warehouse → T-SQL, structured analytics, warehouse-centric modeling
```
Both can participate in the same Fabric ecosystem and OneLake foundation, but workload/persona should drive the choice. citeturn141865search4

## Delta
Delta is the table/storage format used extensively in Fabric Lakehouse. Know ACID transactions, schema enforcement/evolution concepts, time-travel/history concepts and how Spark reads/writes Delta.

## Medallion Architecture
```text
Bronze → raw/landed
Silver → cleaned/conformed
Gold   → business-ready/serving
```
Use separate responsibilities and data contracts across layers. Microsoft provides a specific OneLake Medallion implementation pattern. citeturn141865search8

## Spark in Fabric
Notebooks use PySpark for distributed transformations. Typical flow:
```text
Files/Tables → Notebook → DataFrame transformations → Delta table
```

## Fabric Data Factory
Know pipelines, activities, Copy Activity, Dataflows Gen2, parameters, schedules, incremental ingestion and failure paths.

## Incremental pattern
Use a watermark/CDC/change key, copy/process only changes, merge into curated data, persist successful watermark and make reruns idempotent.

## SQL analytics endpoint
Lakehouse data can be queried through a SQL analytics endpoint. Keep the distinction between engineering with Spark and serving/analysis with SQL.

## Power BI / Direct Lake
Current Microsoft documentation says Direct Lake semantic models load columns from Delta tables in OneLake on demand, rather than first importing a full copy. Direct Lake on OneLake is not coupled to the SQL endpoint; Direct Lake on SQL endpoints can have DirectQuery fallback in cases such as SQL-based security. citeturn141865search6

## Governance
Know RLS, CLS/column-level protection, lineage, monitoring, least privilege, workspace/item permissions and deployment controls. Explain security based on the actual access path rather than saying "RLS applies everywhere".

## CI/CD
Know development/test/production separation, source control/deployment pipeline concepts, parameterized environments and validation before release.

## Interview questions
- What is Fabric?
- What is OneLake?
- Lakehouse vs Warehouse?
- Explain Bronze/Silver/Gold.
- Why Delta?
- How do notebooks and pipelines work together?
- How do you implement incremental ingestion?
- What is Direct Lake?
- How is Power BI connected to curated data?
- How would you secure a department-specific dashboard?
- How would you monitor a failed pipeline?

## Priority
P0 for this training track because Microsoft Fabric is explicitly the specialization. Treat exact Persistent question wording as prediction unless a candidate report confirms it.
