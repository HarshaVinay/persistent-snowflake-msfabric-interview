# Latest Persistent Interview Evidence Update — September 2026

## Purpose

This file records the latest web-researched evidence used to update the Persistent Snowflake_MSFabric interview plan.

## Evidence hierarchy

- **A — Directly reported:** candidate explicitly describes the question as asked in a Persistent interview.
- **B — Reported:** question/pattern appears in a Persistent interview report, often from experienced candidates.
- **C — High-probability:** strong overlap between reported Persistent interviews, current role expectations and the user's curriculum; not confirmed as an exact question.
- **D — General:** useful data-engineering preparation without Persistent-specific evidence.

Do not convert C/D into “confirmed Persistent questions.”

---

## 1. Revature → Persistent pathway evidence

A January 2026 Reddit discussion describes the Revature RRP pathway as role-specific training followed by a Persistent client interview. A participant states that assessments must be cleared and that the interview is expected to focus heavily on what was studied during training. This is candidate testimony, not an official Persistent policy. citeturn0reddit16

### Implication for this preparation

Your **actual Persistent Snowflake_MSFabric curriculum is therefore unusually important**. We should master the curriculum rather than prepare from a generic Data Engineer question list.

---

## 2. Fresh hands-on Persistent Snowflake interview report

A recent Persistent Data Engineer report describes an end-to-end pipeline discussion followed by hands-on Python, SQL, Snowflake and PySpark questions. The reported flow was Source → Azure → Synapse/PySpark → Snowflake. Reported Python tasks included duplicate removal/sorting and finding the second-highest number. SQL included duplicate detection, RANK vs DENSE_RANK and latest-record selection with ROW_NUMBER. Snowflake topics included external stages, file formats, COPY, MERGE, QUALIFY-based deduplication and Streams/CDC. PySpark included null checking, groupBy and RDD map. citeturn1search12

### Classification

| Topic | Evidence | Priority for your track |
|---|---|---:|
| Python basic coding | A | P0 |
| SQL duplicates | A | P0 |
| RANK/DENSE_RANK | A | P0 |
| ROW_NUMBER/latest row | A | P0 |
| Snowflake external stage | A | P0 |
| Snowflake file formats | A | P0 |
| COPY | A | P0 |
| MERGE | A | P0 |
| QUALIFY | A | P0 |
| Streams / CDC | A | P0 |
| PySpark null handling | A | P0 |
| PySpark groupBy | A | P0 |
| RDD map | A | P1 |

This is one of the strongest matches to your curriculum and should directly influence our drills.

---

## 3. Repeated Persistent Azure/PySpark report

Another Persistent Azure Data Engineer report lists RDD/DataFrame/Dataset, PySpark joins, schema evolution, CSV→Parquet coding, memory management, project pipeline explanation, ADF triggers/Integration Runtime, duplicate removal, window functions, SQL optimization and T-SQL error handling. citeturn1search0

### Classification

Most are **A/B** depending on the specific candidate/round. For your preparation, they become P0 because they overlap your curriculum directly.

---

## 4. Repeated architecture pattern

A separate Persistent report includes:

- employee > manager SQL
- weekly critical-order SQL
- nested JSON flattening in PySpark
- cost-efficient ADF + Databricks + ADLS design
- dimensional modeling and sales fact design
- narrow vs wide transformations
- schema evolution
- SCD Type 2 in Spark
- terabyte-scale Spark optimization
- PDF/image ingestion architecture
- Bronze/Silver/Gold
- multi-cloud security/cost
- production and client-management scenarios. citeturn1search2turn1search8

### Classification

These reports are mostly from experienced candidates, so they should be used as **B**, not as proof that a fresher will receive the same depth.

The underlying concepts are nevertheless highly relevant to your training.

---

## 5. Current Persistent Data Engineer guide

A current 2026 Persistent Data Engineer guide highlights Python, SQL, PySpark, Azure Databricks, Snowflake, ETL/ELT, Medallion Architecture, real-time processing, PII handling, masking/encryption, pipeline recovery and SQL optimization. It also describes a typical interview flow of online assessment → technical interviews → HR, while explicitly warning that the exact process varies by client assignment, seniority and technical track. citeturn0search2

Use this as a secondary synthesis, not as stronger evidence than direct candidate reports.

---

## 6. What this changes in our preparation

### P0 — must be interview-ready

1. SQL window functions
2. SQL duplicates/latest-row patterns
3. Python basic coding
4. PySpark DataFrame operations
5. RDD basics
6. Snowflake stages/file formats/COPY
7. MERGE
8. QUALIFY
9. Streams/CDC
10. Snowflake architecture/performance
11. Data modeling
12. SCD Type 2
13. ETL/ELT
14. Spark transformations/shuffle/partitions
15. Schema evolution
16. Medallion Architecture
17. Azure ADF concepts
18. Project end-to-end explanation
19. Microsoft Fabric core architecture
20. Your Cricket and Disaster projects

### P1 — important

- Snowpark
- dbt
- streaming/watermarking/state
- security/RBAC/masking/RLS
- Power BI integration
- Fabric Data Factory
- CI/CD/lineage
- Scala

### P2 — support topics

- deeper cloud pricing theory
- advanced Scala internals
- advanced Pytest internals
- obscure vendor-specific details not present in your curriculum

---

## 7. Interview pattern we should expect

The strongest recurring pattern is:

**Explain your project → solve a small coding problem → solve SQL → explain/implement PySpark → apply Snowflake → discuss pipeline architecture/troubleshooting.**

This pattern is more useful for you than memorizing hundreds of isolated definitions.

---

## Sources

- Revature → Persistent candidate discussion: citeturn0reddit16
- Persistent hands-on Snowflake/PySpark interview: citeturn1search12
- Persistent Azure Data Engineer interview: citeturn1search0
- Persistent Data Engineer multi-round report: citeturn1search2turn1search8
- Current 2026 Persistent Data Engineer guide: citeturn0search2
