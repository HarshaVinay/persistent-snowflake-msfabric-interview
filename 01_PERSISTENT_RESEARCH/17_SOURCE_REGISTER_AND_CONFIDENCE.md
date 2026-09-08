# Persistent Research — Canonical Source Register

Last reviewed: 2026-09-09

## Source hierarchy

### Tier 1 — Official product documentation
Use for technical truth about platform behavior.
- Snowflake Documentation — architecture, micro-partitions, clustering, Time Travel, cloning, loading, security.
- Microsoft Learn — OneLake, Lakehouse, Fabric Warehouse, Direct Lake, OneLake security.

### Tier 2 — Persistent role/company material
Use for current technology and role-alignment signals.
- Persistent Systems data/analytics materials.
- Current Persistent job postings where the role, stack and responsibilities are explicit.

### Tier 3 — Candidate interview reports
Use for interview-pattern detection.
- LinkedIn candidate reports.
- Glassdoor candidate reports.
- AmbitionBox candidate reports.

### Tier 4 — Community discussions
Use for fresher/Revature context and triangulation.
- Reddit and similar community discussions.

## Confidence rules
- **A:** Directly reported question, role and interview context reasonably clear.
- **B:** Reported Persistent question from another experience level or less-complete context.
- **C:** Strong prediction from repeated patterns + curriculum + role requirements.
- **D:** General DE question with no Persistent-specific evidence.

## Mandatory citation discipline
For each externally-derived claim, store:
- source URL
- source type
- publication/update date when available
- role/experience level if known
- whether the question is direct or inferred
- confidence label

## Important caution
Candidate reports are anecdotal. One person's interview is not a guarantee of the user's interview. The handbook should use repeated patterns and syllabus overlap rather than treat an isolated post as a leaked question bank.

## Current high-confidence research themes
- SQL analytical coding: ranking, duplicates, latest records, joins, aggregation.
- Python coding and data manipulation.
- PySpark/Spark transformations, partitions, shuffle, skew, optimization and JSON.
- Snowflake loading and transformation: stages, file formats, COPY, MERGE, QUALIFY, Streams/CDC.
- Data modeling and SCD.
- Azure/ADF and cloud pipeline architecture.
- Project explanation and scenario troubleshooting.

## Current platform sources
- Snowflake micro-partitions/clustering: https://docs.snowflake.com/en/user-guide/tables-clustering-micropartitions
- Snowflake Time Travel/Fail-safe: https://docs.snowflake.com/en/user-guide/data-availability
- Snowflake cloning: https://docs.snowflake.com/en/user-guide/object-clone
- Microsoft OneLake: https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview
- Microsoft Fabric Lakehouse: https://learn.microsoft.com/en-us/fabric/data-engineering/lakehouse-overview
- Direct Lake security: https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-security-integration
- OneLake security: https://learn.microsoft.com/en-us/fabric/onelake/security/get-started-security

## Research maintenance
Do not create a new dated research file for every minor search. Prefer updating the canonical synthesis and source register, then create dated snapshots only when a material interview pattern or platform change is discovered.
