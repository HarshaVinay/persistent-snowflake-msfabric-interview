# Persistent Snowflake_MSFabric Interview Handbook

> **Revature → Persistent Systems | Data Engineering / Snowflake_MSFabric**
>
> **Curriculum-first • Evidence-labelled • Master-notes driven • Project-based**

## Mission

This repository is the single preparation workspace for the Persistent client interview. It combines the user's **exact Revature Persistent SnowFlake MsFabric curriculum**, prior training notes, public Persistent interview evidence, current vendor documentation, and the user's real projects.

The goal is not to collect random questions. The goal is to build **master notes** that can be studied, spoken, coded, challenged, and converted into interview answers.

## Ground truth hierarchy

1. **Authoritative syllabus:** the user's latest pasted Revature Persistent SnowFlake MsFabric curriculum.
2. **User project evidence:** actual repositories and implementation details.
3. **Previous training material:** existing Spark/Snowflake/Python/SQL notes in the user's library.
4. **Interview evidence:** real candidate reports; useful but anecdotal.
5. **Current product truth:** official Snowflake/Microsoft documentation for changing platform behavior.

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
SQL • Python coding • Spark/PySpark • Snowflake • ETL/ELT • data modeling/SCD • projects • Fabric/OneLake/Lakehouse • Azure/ADF

### P1 — Strong working knowledge
DBT • streaming • security/governance • Delta Lake • Power BI • Scala • Airflow/orchestration

### P2 — Supporting coverage
Low-frequency internals and vendor-specific details that are not strongly supported by the syllabus, projects or interview evidence.

## Complete master-note map

| Domain | Master note |
|---|---|
| Master / curriculum | `00_MASTER/11_COMPLETE_CURRICULUM_COVERAGE_MATRIX.md` |
| How to study | `00_MASTER/12_HOW_TO_USE_THIS_HANDBOOK.md` |
| Python | `01_PYTHON/01_PYTHON_COMPLETE_MASTER_NOTES.md` |
| Pandas / NumPy / Pytest | `02_PANDAS_NUMPY_PYTEST/01_PANDAS_NUMPY_PYTEST_MASTER.md` |
| SQL / RDBMS | `02_SQL/04_SQL_COMPLETE_MASTER_NOTES.md` |
| Advanced databases | `04_DATABASE_ADVANCED/01_DATABASE_ADVANCED_MASTER.md` |
| Data engineering | `05_DATA_ENGINEERING/01_DATA_ENGINEERING_COMPLETE_MASTER.md` |
| Spark | `06_SPARK/14_SPARK_COMPLETE_MASTER_NOTES.md` |
| PySpark | `07_PYSPARK/01_PYSPARK_COMPLETE_MASTER.md` |
| Scala | `08_SCALA/01_SCALA_COMPLETE_MASTER.md` |
| Spark Streaming | `08_SPARK_STREAMING/01_SPARK_STREAMING_MASTER.md` |
| Snowflake | `09_SNOWFLAKE/05_SNOWFLAKE_COMPLETE_MASTER_NOTES.md` |
| dbt | `10_DBT/01_DBT_COMPLETE_MASTER.md` |
| Azure / ADF | `11_AZURE/01_AZURE_ADF_COMPLETE_MASTER.md` |
| Microsoft Fabric | `12_MICROSOFT_FABRIC/04_FABRIC_COMPLETE_MASTER_NOTES.md` |
| Airflow | `13_AIRFLOW/01_AIRFLOW_COMPLETE_MASTER.md` |
| BigQuery | `14_BIGQUERY/01_BIGQUERY_COMPLETE_MASTER.md` |
| Projects | `15_PROJECTS/02_PROJECTS_COMPLETE_MASTER.md` |
| Scenarios | `16_SCENARIOS/01_DATA_ENGINEERING_SCENARIO_MASTER.md` |
| Coding | `17_CODING/01_SQL_PYTHON_PYSPARK_MASTER.md` |
| Final interview | `18_FINAL_INTERVIEW/04_FINAL_PERSISTENT_INTERVIEW_MASTER.md` |

## Standard for every master note

Every topic should eventually contain:

**definition → mental model → syntax/code → example → interview answer → follow-ups → scenario → project connection → common mistakes → self-test**

## Study architecture

```text
AUTHORITATIVE CURRICULUM
        ↓
PERSISTENT INTERVIEW EVIDENCE
        ↓
CURRENT PLATFORM VERIFICATION
        ↓
MASTER NOTES
        ↓
CODING / HANDS-ON
        ↓
SCENARIOS
        ↓
PROJECT DEFENCE
        ↓
MOCK INTERVIEW
```

## Project sources

- [Disaster Affected Region Tracker](https://github.com/HarshaVinay/Disaster-Affected-Region-Tracker-Analysis)
- [Cricket Analytics Data Engineering](https://github.com/HarshaVinay/cricket-analytics-data-engineering)

## Current platform references

- [Snowflake — Micro-partitions & Clustering](https://docs.snowflake.com/en/user-guide/tables-clustering-micropartitions)
- [Microsoft — OneLake](https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview)
- [Microsoft — Fabric Lakehouse](https://learn.microsoft.com/en-us/fabric/data-engineering/lakehouse-overview)
- [Microsoft — Fabric Data Factory](https://learn.microsoft.com/en-us/fabric/data-factory/)
- [Microsoft — Direct Lake Security](https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-security-integration)

## Important technical freshness note

Vendor behavior changes. For product facts, current official documentation overrides older training notes. For example, current Snowflake documentation states that standard table data is automatically stored in micro-partitions containing about **50–500 MB of uncompressed data**. citeturn756531search0

Current Microsoft documentation describes OneLake as Fabric's unified logical data lake, Lakehouse as a Delta/Spark/SQL-oriented experience, and Data Factory as supporting pipelines, Copy Activity/Copy jobs, Dataflows Gen2 and monitoring. citeturn625030search6turn756531search11turn756531search4

## Interview discipline

Do not claim production experience you do not have.

Use:
- **“I implemented…”** for project work you actually completed.
- **“I studied…”** for training-only topics.
- **“I would implement…”** for proposed production designs.

## Status

This repository is the structured master handbook. Research and evidence are separated from teaching notes so the preparation remains auditable and maintainable.

**Last audited:** 2026-09-09
