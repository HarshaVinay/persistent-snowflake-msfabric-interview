# Persistent Snowflake Hands-on Drill

## P0 reported areas
A recent Persistent Data Engineer hands-on report describes direct Snowflake questions/coding around:
- external stages
- file formats
- COPY
- MERGE/upsert
- QUALIFY
- duplicate removal
- Streams / CDC
- zero-copy cloning

Source: https://www.linkedin.com/posts/anshu-kumar-987381142_dataengineer-snowflake-sql-activity-7448582660375076864-5r36

## External stage
Know the conceptual flow:
source object storage → external stage → COPY/query → target table.
Be able to explain credentials/integration, file format and error handling at a conceptual level.

## File formats
Know why an explicit FILE FORMAT object can standardize parsing rules such as type, delimiter and header handling.

## COPY INTO
Be ready to explain bulk ingestion into a Snowflake table and the role of a stage/file format.

## MERGE
MERGE supports matched and not-matched branches and is central to upsert/incremental patterns.

## QUALIFY
QUALIFY filters the result of window-function computation, avoiding an extra nesting layer for many dedup/latest-record queries.

## Streams / CDC
A Snowflake stream records table changes for incremental processing. Be able to connect Streams with tasks/procedures or an orchestration layer conceptually.

## Zero-copy cloning
A clone can be created without immediately copying all underlying micro-partition data. It is useful for development, testing, backups/experimentation and environment workflows. Be ready to explain storage/cost implications rather than simply memorizing the phrase.

## Track-specific extensions
Your curriculum also requires:
- virtual warehouses
- micro-partitioning
- pruning
- clustering
- compression
- cache layers
- query profile/performance
- auto-scaling and multi-cluster warehouses
- semi-structured JSON/XML/Avro
- replication/failover/DR
- retention
- UDFs
- stored procedures
- Snowpark
- RBAC
- masking and row-level security

## Interview scenario
**Question:** A Snowflake incremental pipeline is producing duplicates. What would you do?

Answer structure:
1. establish the business key and target grain;
2. inspect source duplicates;
3. deduplicate with ROW_NUMBER/QUALIFY where appropriate;
4. use MERGE for deterministic upsert logic;
5. use Streams for change capture when applicable;
6. make the load idempotent;
7. add data-quality checks and monitoring.

## Evidence rule
The hands-on items above are reported by a candidate. Do not claim that every Persistent interviewer asks the same Snowflake questions.