# Repository Audit — 2026-09-09

## Audit scope
This audit reviews the handbook structure against:
1. The user's exact Revature Persistent Snowflake_MSFabric curriculum.
2. The two project repositories.
3. Current Persistent Data Engineer role/interview signals found on the web.
4. Current official Snowflake and Microsoft Fabric documentation.
5. The handbook's organization, evidence quality, duplication risk, and missing coverage.

## Current assessment
The repository has a solid research foundation but the earlier structure risked becoming repetitive because multiple dated web-update files covered similar evidence. The professional version should use a small number of canonical documents and treat dated research notes as supporting records.

## Canonical hierarchy
- `00_MASTER/` = scope, standards, curriculum map, readiness plan.
- `01_PERSISTENT_RESEARCH/` = external evidence and source register.
- `02_SQL/` through `14_BIGQUERY/` = technical knowledge.
- `15_PROJECTS/` = project-specific implementation and interview defense.
- `16_SCENARIOS/` = production-style problem solving.
- `17_CODING/` = hands-on coding drills.
- `18_FINAL_INTERVIEW/` = final revision and mock interviews.

## Important audit finding
The research directory contains several dated update files. They should not be treated as separate curricula. The canonical evidence synthesis should consolidate them. This keeps the handbook readable and reduces contradictory or stale advice.

## Priority corrections
### P0 — required
- Make the user's exact pasted curriculum the immutable syllabus baseline.
- Separate reported interview questions from predictions.
- Keep fresher evidence distinct from experienced-candidate evidence.
- Add source dates and confidence notes.
- Build complete SQL, Spark/PySpark, Snowflake, Fabric, project and scenario content.
- Add a final interview execution plan.

### P1 — important
- Add Azure/ADF, dbt, security/governance, orchestration and project-specific cross-examination.
- Add cross-technology comparison matrices.
- Add troubleshooting playbooks.

### P2 — supporting
- Scala, BigQuery, Pytest, visualization and secondary cloud material.

## Current external evidence pattern
Recent Persistent Data Engineer interview guidance emphasizes PySpark transformations, SQL window functions, storage optimization, cloud data architecture/ETL, and project/scenario reasoning. The source is a secondary interview guide, so it is useful for pattern detection but not equivalent to an official Persistent question bank. [Dataford](https://dataford.io/interview-guides/persistent-systems/data-engineer).

## Current official platform corrections
Snowflake documentation states that all Snowflake tables are automatically organized into micro-partitions, with metadata enabling pruning; clustering is a separate table-level strategy that can improve data organization for very large tables. [Snowflake micro-partitions and clustering](https://docs.snowflake.com/en/user-guide/tables-clustering-micropartitions).

Snowflake also documents Time Travel and Fail-safe as different mechanisms, with Time Travel supporting historical querying/restoration/cloning during retention and Fail-safe providing Snowflake-managed recovery after Time Travel. [Snowflake data availability](https://docs.snowflake.com/en/user-guide/data-availability).

Microsoft currently documents OneLake as Fabric's unified data lake, and Fabric Lakehouse as a Delta-based environment supporting Spark and SQL access. [OneLake](https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview), [Lakehouse](https://learn.microsoft.com/en-us/fabric/data-engineering/lakehouse-overview).

## Professionalization standard
Every new technical document should contain:
- Scope
- Curriculum mapping
- Priority
- Core concepts
- Examples/code where appropriate
- Interview questions
- Scenario questions
- Common traps
- Project connection
- Source/evidence notes
- Last reviewed date

## Definition of done
The handbook is ready only when every curriculum section has either:
- a complete interview-ready note, or
- a deliberate low-priority marker explaining why only overview depth is required.
