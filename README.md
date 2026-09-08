# Persistent Snowflake_MSFabric Interview Handbook

> **Revature → Persistent Systems | Data Engineering / Snowflake_MSFabric**
>
> Curriculum-first • Evidence-labelled • Project-driven • Interview-ready

## Mission

This repository is the single preparation workspace for the Persistent client interview. It combines the user's **exact Revature Persistent SnowFlake MsFabric curriculum**, public Persistent interview evidence, current Snowflake/Fabric documentation, previous training notes, and the user's real projects.

The goal is not to collect random interview questions. The goal is to build answers that survive technical follow-ups, coding exercises, project cross-examination, and architecture scenarios.

## Source of truth

1. **Authoritative syllabus:** the user's latest pasted Revature Persistent SnowFlake MsFabric curriculum.
2. **Primary project evidence:**
   - [Disaster Affected Region Tracker](https://github.com/HarshaVinay/Disaster-Affected-Region-Tracker-Analysis)
   - [Cricket Analytics Data Engineering](https://github.com/HarshaVinay/cricket-analytics-data-engineering)
3. **Interview evidence:** candidate reports and current Persistent role signals.
4. **Technical truth for changing platforms:** official Snowflake and Microsoft documentation.

## Evidence labels

| Label | Meaning |
|---|---|
| **A** | Directly reported Persistent interview question/context |
| **B** | Reported Persistent question, mainly from experienced candidates |
| **C** | High-probability prediction from curriculum + role/interview overlap |
| **D** | General interview preparation without Persistent-specific evidence |

**Rule:** C/D material must never be presented as a confirmed Persistent question.

## Priority model

### P0 — Know cold
SQL • Python coding • Spark/PySpark • Snowflake • ETL/ELT • data modeling/SCD • project defence • Fabric/OneLake/Lakehouse • Azure/ADF

### P1 — Important
DBT • streaming • security/governance • Delta Lake • Power BI • Scala • orchestration/Airflow

### P2 — Supporting
Obscure internals, low-frequency features and vendor details that are not strongly supported by the syllabus, project or evidence.

## Handbook structure

| Section | Purpose |
|---|---|
| `00_MASTER` | Scope, audit, study order, writing/evidence standards |
| `01_PERSISTENT_RESEARCH` | Interview evidence and source register |
| `02_SQL` | SQL fundamentals, analytics, coding and optimization |
| `03_PYTHON` | Python foundations and interview coding |
| `04_PANDAS_NUMPY_PYTEST` | Data wrangling and testing |
| `05_DATA_ENGINEERING` | ETL/ELT, architecture, modeling, SCD, CDC |
| `06_SPARK` | Spark engine, execution and optimization |
| `07_PYSPARK` | Practical DataFrame/JSON/join/window coding |
| `08_SCALA` | Scala curriculum and interview coverage |
| `09_SNOWFLAKE` | Snowflake specialization |
| `10_DBT` | dbt + Snowflake transformation engineering |
| `11_AZURE` | Azure/ADLS/ADF concepts |
| `12_MICROSOFT_FABRIC` | Fabric/OneLake/Lakehouse/Warehouse/BI |
| `13_AIRFLOW` | Orchestration support |
| `14_BIGQUERY` | Cloud warehouse support |
| `15_PROJECTS` | Project implementation and defence |
| `16_SCENARIOS` | Troubleshooting and architecture |
| `17_CODING` | Dedicated coding practice |
| `18_FINAL_INTERVIEW` | Final revision and mock interviews |

## Canonical workflow

```text
Curriculum
   ↓
Persistent evidence
   ↓
Technical verification
   ↓
Concept + mental model
   ↓
Coding / implementation
   ↓
Scenario / troubleshooting
   ↓
Project connection
   ↓
Follow-up questions
   ↓
Mock interview
```

## Research discipline

Public interview posts are anecdotal and can vary by role, client, seniority and date. Use repeated patterns rather than isolated claims. Current vendor documentation takes precedence for product behavior that changes over time.

### Current platform references
- [Snowflake micro-partitions and clustering](https://docs.snowflake.com/en/user-guide/tables-clustering-micropartitions)
- [Snowflake Time Travel and Fail-safe](https://docs.snowflake.com/en/user-guide/data-availability)
- [Snowflake cloning](https://docs.snowflake.com/en/user-guide/object-clone)
- [Microsoft OneLake](https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview)
- [Microsoft Fabric Lakehouse](https://learn.microsoft.com/en-us/fabric/data-engineering/lakehouse-overview)
- [Direct Lake security](https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-security-integration)
- [OneLake security](https://learn.microsoft.com/en-us/fabric/onelake/security/get-started-security)

## Interview answer standard

For concepts:
**definition → mechanism → example → when/why**

For comparisons:
**dimension → option A → option B → trade-off → selection rule**

For coding:
**clarify → implement → edge cases → complexity → explain aloud**

For scenarios:
**requirements → volume/SLA → design → quality → failure recovery → security → monitoring → cost/performance**

## Status

This is an actively maintained preparation handbook. The detailed audit and source register explain what is confirmed, what is predicted, and where further depth is required.

**Last audited:** 2026-09-09
