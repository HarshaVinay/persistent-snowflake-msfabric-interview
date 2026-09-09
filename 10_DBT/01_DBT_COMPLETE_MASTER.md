# dbt Complete Master Notes

## Purpose
Use dbt to build, test, document and orchestrate SQL-based transformation models, especially in analytical warehouses such as Snowflake.

## Core concepts
- Project: dbt code/configuration unit.
- Model: SQL transformation that becomes a view/table/incremental object according to materialization.
- Source: declared upstream data source.
- Seed: version-controlled CSV data loaded by dbt.
- `ref()`: references another dbt model and creates a dependency in the DAG.
- Tests: assertions about data quality.
- Documentation: generated descriptions/lineage metadata.

## Materializations
- View: lightweight logical layer; query runs when consumed.
- Table: materialized result; faster reads at the cost of build/storage.
- Incremental: process only new/changed data after the initial build.
- Ephemeral: reusable SQL logic that is inlined rather than persisted.

## DAG mental model
`source → staging → intermediate → marts`.
A model references upstream models using `ref()`; dbt determines execution order from the dependency graph.

## Incremental design
A reliable incremental model needs:
- stable business/technical key
- deterministic change condition
- watermark/updated timestamp or CDC input
- strategy for late-arriving updates
- strategy for deletes when required
- idempotent behavior

## Snapshots / SCD
Snapshots preserve historical versions of records and can support SCD-style analysis. Know the business key, tracked attributes, valid periods and current version logic.

## Tests
Common tests:
- unique
- not_null
- accepted_values
- relationships
- custom business-rule tests

## Snowflake integration
Typical flow:
`raw tables → dbt staging → transformations → marts → BI`.

## Interview questions
1. Why dbt instead of handwritten SQL scripts?
2. What is `ref()`?
3. View vs table vs incremental?
4. How do you build SCD history?
5. How do tests help data quality?
6. How would you troubleshoot a failed incremental model?

## Interview-safe statement
Your curriculum marks advanced dbt as a brief overview, so prioritize fundamentals, model dependencies, tests, materializations, incremental loading, snapshots and Snowflake integration rather than obscure dbt internals.
