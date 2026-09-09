# Data Engineering Complete Master Notes

## Core idea
Data engineering turns raw data into reliable, usable data products through ingestion, storage, transformation, quality, governance, orchestration and serving.

## Data types
- Structured: rows/columns, fixed schema.
- Semi-structured: JSON/XML/Avro; schema is flexible or embedded.
- Unstructured: documents, images, audio, video.

## OLTP vs OLAP
OLTP: transactional, frequent small writes, normalized design, operational consistency.
OLAP: analytical, large scans/aggregations, dimensional/denormalized models and read optimization.

## Data lake vs data warehouse
Data lake: inexpensive scalable storage for raw and varied data, flexible processing.
Warehouse: curated structured analytical data optimized for SQL/reporting.
Lakehouse combines lake-style storage/flexibility with table/transaction/analytics capabilities.

## DWH architecture
A common conceptual flow:
`sources → ingestion → staging/raw → transformation → curated warehouse → semantic/reporting`.
ODS sits between operational sources and analytical layers when near-current integrated data is required. A data mart is a subject-oriented subset for a business domain.

## ETL vs ELT
ETL transforms before loading. ELT loads raw/near-raw data first and transforms in the target analytical platform. Modern cloud warehouses often favor ELT because compute and storage can scale independently.

## Pipeline principles
- Idempotency: repeated execution should not incorrectly duplicate results.
- Incremental processing: process new/changed data instead of everything.
- Backfills: deliberately recompute historical windows.
- Retryability: transient failures can be retried safely.
- Observability: logs, metrics, row counts, freshness, failures.

## Incremental patterns
Common approaches:
- timestamp watermark
- monotonically increasing ID
- CDC/change streams
- source-side modified timestamp
- partition-by-date processing

Never assume a timestamp is sufficient unless late updates and clock semantics are understood.

## CDC
Change Data Capture identifies inserts/updates/deletes. A reliable pipeline uses a business key plus operation/time metadata and applies deterministic merges.

## Data quality
Validate:
- schema
- nullability
- uniqueness
- referential integrity
- accepted values
- ranges
- freshness
- volume anomalies
- duplicate rates

## Dimensional modeling
Fact = measurable business event at a declared grain.
Dimension = descriptive context such as customer, product, date.

### Star schema
Facts connect directly to dimensions. Simple for BI and often efficient for analytical querying.

### Snowflake schema
Dimensions are further normalized. Can reduce redundancy but increases join complexity.

## Grain
The most important modeling question is: **What does one row represent?**
Examples:
- one order line
- one cricket delivery
- one disaster-region-event combination

A correct grain prevents double-counting.

## SCD
- Type 0: retain original value.
- Type 1: overwrite.
- Type 2: preserve history with versions/effective dates/current flag.
- Type 3: limited history using additional columns.

### SCD2 conceptual flow
`incoming change → identify business key → compare tracked attributes → expire old version → insert new version → keep current indicator.`

## Data cleansing
Standardize formats, parse dates, convert numeric fields, deduplicate, handle invalid values and apply documented business rules.

## Cloud service models
IaaS: infrastructure. PaaS: managed platform. SaaS: complete application. For data engineering, emphasize managed storage, compute, orchestration, identity and monitoring rather than vendor trivia.

## Scenario: design daily analytics
`source → ingestion → raw storage → transform → curated layer → warehouse/semantic layer → BI`.
Then discuss incremental loads, retries, quality checks, lineage, security, monitoring and cost.

## Persistent interview angle
Be ready to defend grain, SCD2, incremental loading, schema evolution, data quality, ETL/ELT and project architecture. These concepts connect directly to both of your projects and recurring Persistent data-engineering interview themes.
