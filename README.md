# Persistent Snowflake_MSFabric Interview Handbook

> **Revature → Persistent Systems | Data Engineering / Snowflake_MSFabric**
>
> **Curriculum-first • Evidence-labelled • Master-notes driven • Project-based**

## Mission

This repository is the single preparation workspace for the Persistent client interview. It combines the user's **exact Revature Persistent SnowFlake MsFabric curriculum**, previous training notes, public Persistent interview evidence, current vendor documentation, and the user's two projects.

The goal is to build answers that survive technical follow-ups, coding exercises, project cross-examination, troubleshooting and architecture scenarios.

## Ground truth hierarchy

1. **Authoritative syllabus:** the user's latest pasted Revature Persistent SnowFlake MsFabric curriculum.
2. **Project evidence:** actual implementation in the user's two project repositories.
3. **Previous training material:** existing Spark, Snowflake, Python, SQL and related notes.
4. **Interview evidence:** candidate reports and current Persistent role signals.
5. **Technical truth:** current official Snowflake and Microsoft documentation.

## Evidence labels

| Label | Meaning |
|---|---|
| **A** | Directly reported Persistent interview question/context |
| **B** | Reported Persistent question, mainly from experienced candidates |
| **C** | High-probability prediction from curriculum + role + recurring patterns |
| **D** | General interview preparation |

**Never present C/D as confirmed Persistent questions.**

## Priority model

### P0 — Know cold
SQL • Python coding • Spark/PySpark • Snowflake • ETL/ELT • dimensional modeling/SCD • project defence • Fabric/OneLake/Lakehouse • Azure/ADF

### P1 — Strong working knowledge
dbt • streaming • security/governance • Delta Lake • Power BI • Scala • Airflow/orchestration

### P2 — Supporting coverage
Lower-frequency internals and vendor details that are not strongly supported by the syllabus, projects or evidence.

## Canonical navigation

Start here: `00_MASTER/16_CANONICAL_NAVIGATION.md`

### Core master notes

| Domain | Canonical note |
|---|---|
| SDLC / Git | `01_SDLC_GIT/01_SDLC_GIT_MASTER.md` |
| Python | `01_PYTHON/01_PYTHON_COMPLETE_MASTER_NOTES.md` |
| Pandas / NumPy / Pytest | `02_PANDAS_NUMPY_PYTEST/01_PANDAS_NUMPY_PYTEST_MASTER.md` |
| SQL | `02_SQL/04_SQL_COMPLETE_MASTER_NOTES.md` |
| Advanced database | `04_DATABASE_ADVANCED/01_DATABASE_ADVANCED_MASTER.md` |
| Data engineering | `05_DATA_ENGINEERING/01_DATA_ENGINEERING_COMPLETE_MASTER.md` |
| Spark | `06_SPARK/14_SPARK_COMPLETE_MASTER_NOTES.md` |
| PySpark | `07_PYSPARK/01_PYSPARK_COMPLETE_MASTER.md` |
| Scala | `08_SCALA/01_SCALA_COMPLETE_MASTER.md` |
| Spark streaming | `08_SPARK_STREAMING/01_SPARK_STREAMING_MASTER.md` |
| Snowflake | `09_SNOWFLAKE/05_SNOWFLAKE_COMPLETE_MASTER_NOTES.md` |
| Snowpark / security | `09_SNOWFLAKE/02_SNOWPARK_SECURITY_ORCHESTRATION_MASTER.md` |
| dbt | `10_DBT/01_DBT_COMPLETE_MASTER.md` |
| Azure / ADF | `11_AZURE/01_AZURE_ADF_COMPLETE_MASTER.md` |
| Microsoft Fabric | `12_MICROSOFT_FABRIC/04_FABRIC_COMPLETE_MASTER_NOTES.md` |
| Fabric pipelines / BI | `12_MICROSOFT_FABRIC/03_FABRIC_DATA_FACTORY_WAREHOUSE_POWERBI_MASTER.md` |
| Airflow | `13_AIRFLOW/01_AIRFLOW_COMPLETE_MASTER.md` |
| BigQuery | `14_BIGQUERY/01_BIGQUERY_COMPLETE_MASTER.md` |
| Projects | `15_PROJECTS/02_PROJECTS_COMPLETE_MASTER.md` |
| Scenarios | `16_SCENARIOS/01_DATA_ENGINEERING_SCENARIO_MASTER.md` |
| Coding | `17_CODING/01_SQL_PYTHON_PYSPARK_MASTER.md` |
| Final interview | `18_FINAL_INTERVIEW/04_FINAL_PERSISTENT_INTERVIEW_MASTER.md` |

## Research

Canonical research: `01_PERSISTENT_RESEARCH/17_SOURCE_REGISTER_AND_CONFIDENCE.md`

Interview-pattern synthesis: `01_PERSISTENT_RESEARCH/18_MASTER_INTERVIEW_PATTERNS.md`

Repository audit: `00_MASTER/15_REPOSITORY_AUDIT_2026-09-09.md`

Content status: `00_MASTER/17_CONTENT_STATUS.md`

## Standard for every topic

```text
Curriculum
  ↓
Persistent evidence
  ↓
Current technical verification
  ↓
Master note
  ↓
Coding / hands-on
  ↓
Scenario
  ↓
Project connection
  ↓
Follow-ups
  ↓
Mock interview
```

Every P0 topic should eventually support:

**definition → mental model → implementation → performance/security → scenario → project connection → common mistakes → self-test**

## Projects

- [Disaster Affected Region Tracker](https://github.com/HarshaVinay/Disaster-Affected-Region-Tracker-Analysis)
- [Cricket Analytics Data Engineering](https://github.com/HarshaVinay/cricket-analytics-data-engineering)

## Current technical references

### Snowflake
- [Micro-partitions & clustering](https://docs.snowflake.com/en/user-guide/tables-clustering-micropartitions)
- [Time Travel](https://docs.snowflake.com/en/user-guide/data-time-travel)
- [Time Travel & Fail-safe](https://docs.snowflake.com/en/user-guide/data-availability)
- [Fail-safe](https://docs.snowflake.com/en/user-guide/data-failsafe)
- [CREATE CLONE](https://docs.snowflake.com/en/sql-reference/sql/create-clone)
- [Cloning considerations](https://docs.snowflake.com/en/user-guide/object-clone)
- [Streams and Tasks](https://docs.snowflake.com/en/user-guide/data-pipelines-intro)

### Microsoft Fabric
- [OneLake overview](https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview)
- [Lakehouse overview](https://learn.microsoft.com/en-us/fabric/data-engineering/lakehouse-overview)
- [Medallion architecture](https://learn.microsoft.com/en-us/fabric/onelake/onelake-medallion-lakehouse-architecture)
- [Data storage options](https://learn.microsoft.com/en-us/fabric/fundamentals/store-data)
- [Direct Lake](https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-how-it-works)
- [Direct Lake security](https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-security-integration)
- [OneLake security](https://learn.microsoft.com/en-us/fabric/onelake/security/get-started-security)
- [OneLake RLS/CLS](https://learn.microsoft.com/en-us/fabric/onelake/security/row-level-security)

## Interview discipline

Do not claim production experience you do not have.

Use:
- **“I implemented…”** for work you actually completed.
- **“I studied…”** for training-only material.
- **“I would implement…”** for proposed production designs.

## Freshness rule

Current official product documentation overrides stale platform details in older training notes. The repository's source register records the authoritative URLs and evidence rules.

## Status

**Repository structure:** stable.

**Current work:** deepen P0 content and practice; do not create redundant research notes unless a material new finding appears.

**Last audited:** 2026-09-09
