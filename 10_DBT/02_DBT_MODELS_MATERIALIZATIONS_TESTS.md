# dbt Models, Materializations, Sources & Tests

## dbt mental model
```text
Source systems
    ↓
Snowflake raw/staging
    ↓
 dbt models
    ↓
curated analytics
    ↓
BI / downstream
```

dbt focuses primarily on transforming data with SQL and managing the transformation project as code.

## Models
A model is a SQL-based transformation managed by dbt.

## `ref()`
`ref('model_name')` creates dependency-aware references between models and contributes to the project DAG.

## Sources
Sources define upstream raw inputs and make lineage and testing more explicit.

## Seeds
CSV-like files committed with the project that dbt can load for controlled reference data.

## Materializations
Know the trade-offs:
- **view** — query definition, lightweight storage, recomputed when read.
- **table** — persisted relation, more storage/write work, fast reads.
- **incremental** — process only new/changed data according to model logic.
- **ephemeral** — reusable SQL logic that is not persisted as a relation.

## Tests
Common generic tests:
- uniqueness
- not null
- accepted values
- relationships

Also understand custom SQL tests for business rules.

## Snapshots
Snapshots preserve historical changes to records and are useful for SCD-style history when configured correctly.

## Documentation
Good dbt projects document models, columns and sources and expose dependency lineage.

## Snowflake integration
dbt commonly uses Snowflake as its transformation target in this curriculum. Warehouse choice, model materialization and incremental strategy affect cost and runtime.

## Interview scenario
**A fact table is 2 TB and only yesterday's records change.**
Use an incremental model rather than rebuilding the complete table every run, but define the change boundary and merge/deduplication behavior carefully.

## Important curriculum note
Your curriculum calls advanced dbt a brief overview. Be strong on concepts, DAG/ref, materializations, testing, snapshots, incremental logic and Snowflake integration; do not overfocus on obscure dbt internals.
