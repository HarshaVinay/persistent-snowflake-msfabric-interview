# Fabric Data Factory, Warehouse, T-SQL & Power BI

## Data Factory in Fabric
Use pipelines to orchestrate ingestion and workflow dependencies.

Typical flow:
```text
Source
 ↓
Copy Activity
 ↓
Bronze/Landing
 ↓
Notebook / transformation
 ↓
Silver
 ↓
Curated Gold
 ↓
Warehouse / semantic model
 ↓
Power BI
```

## Copy Activity
Moves data between supported source and target systems. It is an ingestion/movement tool, not a replacement for distributed transformation logic.

## Dataflows Gen2
A low-code transformation/ingestion experience useful for repeatable data preparation. Use it when it fits the team's complexity and skill profile; use notebooks/Spark for heavier custom distributed transformations.

## Parameterization
Parameters make pipelines reusable across dates, paths, tables and environments.

## Scheduling
Separate schedule/orchestration from the transformation logic so execution can be changed without rewriting business transformations.

## Fabric Warehouse
Use T-SQL for relational analytical serving. Build a clean Gold layer and model facts/dimensions at the appropriate grain.

## Power BI
Typical path:
```text
Gold / Warehouse / Lakehouse
        ↓
Semantic model
        ↓
Measures + relationships
        ↓
Power BI report
```

## Direct Lake
Current Microsoft documentation says Direct Lake semantic models load columns from Delta tables in OneLake as needed rather than importing the data in the traditional sense. Direct Lake on OneLake uses OneLake directly and does not use DirectQuery fallback; Direct Lake on SQL endpoints can fall back to DirectQuery in some cases.

Sources:
- https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-how-it-works
- https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-develop

## RLS / CLS
- RLS limits rows by security rule.
- CLS limits columns/column-level access where the platform/security feature supports it.

## Interview scenario
**Business wants dashboards with fresh data.**
Explain the trade-off between refresh/import, DirectQuery and Direct Lake based on data location, freshness, workload, governance and performance. Do not claim one mode is universally best.
