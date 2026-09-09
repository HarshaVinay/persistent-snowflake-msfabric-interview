# Microsoft Fabric Complete Master Notes

## What is Microsoft Fabric?
Fabric is a SaaS analytics platform that brings data engineering, Data Factory, data science, data warehousing, real-time analytics and Power BI into an integrated environment.

## OneLake
OneLake is Fabric's unified logical data lake for the organization. Current Microsoft documentation describes it as the single place for analytics data, with Fabric workloads using it as the shared data foundation. citeturn625030search6

## Lakehouse
A Fabric Lakehouse provides a Files area and a Tables area. Current documentation describes Delta tables, Spark/SQL access and built-in integration with Power BI and pipelines. citeturn756531search11

## Warehouse
Fabric Warehouse is the SQL-centric analytical serving layer. Be ready to explain when analysts/BI users benefit from T-SQL and dimensional models.

## Lakehouse vs Warehouse
| Lakehouse | Warehouse |
|---|---|
| Spark-first engineering | T-SQL-first analytics |
| Structured + broader lake data | Primarily structured analytical data |
| Files + Delta tables | Warehouse tables/model |
| Strong fit for data engineering | Strong fit for SQL/BI serving |

Current Microsoft documentation states both are backed by OneLake/Delta-based storage, but their development tools and workload patterns differ. citeturn756531search11

## Delta
Delta tables provide table semantics on lake storage, including ACID-oriented transactions, schema management and time-travel concepts. In Fabric Lakehouse, Delta is the core table format documented for tables. citeturn756531search11

## Spark in Fabric
Fabric notebooks can use PySpark for data engineering. The engineering pattern is usually:
`OneLake → notebook → DataFrame transformation → Delta table`.

## Medallion Architecture
Bronze = raw/landed data.
Silver = cleaned/conformed data.
Gold = business-ready serving data.

Example:
`CSV/API → Bronze → PySpark cleaning → Silver → business aggregation/modeling → Gold → Warehouse/semantic model → Power BI`.

## OneLake shortcuts
A shortcut points to data without creating another logical edge copy. Microsoft documents shortcuts as a way to connect internal or external data sources through OneLake. citeturn625030search5

## Data Factory in Fabric
Fabric Data Factory supports pipelines, Copy activity/Copy jobs, Dataflows Gen2, scheduling and monitoring. Current documentation also supports incremental copy patterns. citeturn756531search4turn756531search7

## Copy Activity
Copy Activity connects to source/destination stores, moves data, handles mapping/conversion and provides monitoring. citeturn756531search1

## Dataflows Gen2
Dataflows Gen2 provide visual Power Query-based ingestion/transformation. Current Microsoft documentation recommends Gen2 for new work and notes modern CI/CD/Git integration. citeturn756531search10

## SQL analytics endpoint
A Lakehouse provides a SQL analytics endpoint so SQL users can query tables without converting the entire engineering workload into T-SQL.

## Direct Lake
Direct Lake semantic models can read Delta data directly from OneLake rather than requiring a traditional imported copy. Current Microsoft documentation explains that security behavior depends on whether the model accesses data through OneLake or SQL endpoints. citeturn756531search8turn625030search2

## Governance/security
OneLake security is split between control-plane permissions and data-plane permissions. Current Microsoft documentation describes granular security down to tables/folders, rows and columns, with Microsoft Entra ID used for authentication. citeturn625030search0turn625030search3

## RLS / CLS / OLS
- RLS: restrict rows.
- CLS: restrict columns.
- OLS: restrict objects such as tables/folders.
Current OneLake documentation describes these granular controls. citeturn625030search7

## Power BI
Use curated Gold/warehouse data through a semantic model. Know relationships, measures, RLS and Direct Lake at a conceptual level.

## CI/CD and monitoring
Use Git/deployment concepts, parameterization, environment separation, pipeline monitoring and data-quality checks. The interview goal is to show production discipline, not merely UI familiarity.

## Interview question
**Design a Fabric data pipeline.**
“Sources land in OneLake, raw data is kept in Bronze, PySpark/Dataflow transformations produce Silver, business rules produce Gold, and the curated data is served through a Warehouse or semantic model for Power BI. I would add incremental processing, data-quality checks, retries, monitoring, security and CI/CD.”
