# dbt Interview Master

## Core mental model
Sources/seeds → models → dependency DAG → tests/docs → materialized relations in Snowflake.

## Must know
- Project structure.
- `source()` vs `ref()`.
- Models.
- Seeds.
- Materializations: view, table, incremental, ephemeral concept.
- Generic/schema tests and singular tests.
- Documentation and lineage.
- Incremental models and merge strategy.
- Snapshots for historical changes/SCD use cases.

## Interview questions
1. Why dbt instead of putting every transformation in stored procedures?
2. What does `ref()` provide?
3. View vs table vs incremental.
4. How do you design an incremental model safely?
5. How do snapshots preserve history?
6. How do tests improve data quality?
7. How does dbt fit with Snowflake?

## Track note
The curriculum labels advanced dbt as a brief overview. Focus on practical concepts and integration rather than obscure internals.