# Microsoft Fabric Master Interview Guide

## OneLake
OneLake is Fabric's unified logical data lake for the organization and is automatically provisioned with a Fabric tenant. Fabric engines can work with shared data rather than maintaining duplicated copies. citeturn969057search8

## Lakehouse
Fabric Lakehouse combines lake-scale storage with table/query capabilities. It uses Delta and supports Spark plus SQL access. Microsoft positions Lakehouse for data engineering/data science/medallion scenarios and Warehouse for SQL-first BI/dimensional-modeling scenarios. citeturn969057search0

## End-to-end
Sources → Data Factory/shortcut/mirroring/streaming → Bronze → Silver → Gold → Warehouse/semantic model → Power BI.

## Medallion
Bronze: raw/landed. Silver: validated, cleaned, deduplicated and conformed. Gold: business-ready and optimized for consumption. Microsoft's current tutorial uses this exact flow. citeturn969057search2turn969057search4

## Data Engineering workload
Fabric Data Engineering provides Lakehouse, notebooks, pipelines and Spark job definitions for batch/stream processing. citeturn969057search7

## Warehouse vs Lakehouse
Lakehouse: Spark-first, mixed structured/unstructured, medallion/data engineering. Warehouse: T-SQL-first, structured, dimensional/BI. Both can be combined in one workspace. citeturn969057search0

## Direct Lake
Direct Lake reads Delta data directly from OneLake rather than requiring a traditional import of the data. Current Microsoft docs describe security integration with OneLake roles and effective identity. citeturn969057search5turn785498search1

## Security
Current OneLake security supports object/table/folder controls and row/column-level security. OneLake RLS/CLS are data-plane controls and have role/permission constraints that matter in real deployments. citeturn785498search0turn785498search5

## Interview questions
- What is Fabric?
- What is OneLake?
- Lakehouse vs Warehouse?
- Why Delta?
- Explain Bronze/Silver/Gold.
- How would you build an incremental pipeline?
- How do you connect Power BI?
- Direct Lake vs import/direct query?
- How do you secure PII?
- How do you monitor and recover pipelines?