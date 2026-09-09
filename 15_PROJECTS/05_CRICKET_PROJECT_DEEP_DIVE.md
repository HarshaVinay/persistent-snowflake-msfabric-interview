# Cricket Analytics Data Engineering — Interview Deep Dive

Repository: https://github.com/HarshaVinay/cricket-analytics-data-engineering

## Why this is valuable
This project overlaps strongly with the training track because the repository includes landing data, SQL, Airflow, dbt, tests, documentation and an application/analytics layer.

## Interview explanation
Present the project as a production-style analytics pipeline:
```text
Source cricket data
      ↓
Landing / raw layer
      ↓
Ingestion / orchestration
      ↓
Data quality + transformations
      ↓
Curated analytical models
      ↓
dbt / SQL serving
      ↓
Analytics application / reporting
```

## Airflow
Explain why orchestration is separate from transformation:
- schedules and dependencies;
- retries and failure routing;
- task-level observability;
- controlled reruns.

## dbt
Explain models, dependencies via `ref()`, tests, materializations, documentation and incremental design.

## SQL/data modeling
Be ready to define the grain of match, innings, player and ball-level tables. Explain facts vs dimensions and how joins avoid double counting.

## Ball-by-ball scale question
If delivery volume grows substantially:
- store raw immutable files;
- use columnar formats;
- partition by useful date/competition dimensions where justified;
- process transformations with Spark when volume requires it;
- build curated fact/dimension models;
- use incremental loading rather than full rebuilds.

## Snowflake redesign
```text
Landing files
 ↓
Snowflake stage
 ↓
COPY into raw
 ↓
validation/dedup
 ↓
MERGE curated facts/dims
 ↓
analytics
```
Use Streams/tasks or orchestration where the actual implementation requires incremental CDC-style processing.

## Fabric redesign
```text
Landing
 ↓
OneLake / Bronze
 ↓
PySpark / Silver
 ↓
Gold
 ↓
Warehouse / semantic model
 ↓
Power BI
```

## Questions to rehearse
1. Why Airflow?
2. Why dbt?
3. What does one delivery row represent?
4. How do you handle late-arriving data?
5. How do you prevent duplicate deliveries?
6. How would you implement SCD for players/teams?
7. How would you process nested data?
8. How would you migrate this to Snowflake?
9. How would you implement it in Fabric?
10. What would you monitor?
