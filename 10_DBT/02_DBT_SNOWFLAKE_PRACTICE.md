# dbt + Snowflake Practice

## Typical flow
Source tables → dbt staging models → intermediate models → marts → tests/docs → Snowflake relations.

## Incremental pattern
Use a stable unique key and a reliable change/watermark column. On each run, select only new/changed records and merge safely. Plan for late-arriving updates and reruns.

## Snapshot/SCD
A snapshot preserves versions of a business entity over time. Know how it differs from a normal incremental model and how a Type 2 dimension represents historical validity.

## Tests
Uniqueness, not-null, accepted values and relationships are core tests. Add business-rule tests for critical metrics.

## Questions
- Why dbt in a Snowflake project?
- How does `ref()` build dependencies?
- How do incremental models reduce work?
- How would you test a fact table?
- How would you document lineage?