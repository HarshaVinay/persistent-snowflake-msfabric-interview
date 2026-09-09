# Project 2 — Cricket Analytics Data Engineering Master Notes

## Repo
https://github.com/HarshaVinay/cricket-analytics-data-engineering

## Repository areas
Current repository structure includes `landing`, `airflow`, `cricket_dbt`, `sql`, `tests`, `docs`, and `streamlit_app`.

## One-line answer
"I built a cricket analytics data-engineering pipeline around teams, players, matches and deliveries, with landing/curation, SQL analytics, Airflow orchestration, dbt transformations/tests and an application-facing analytics layer."

## Architecture to explain
```text
Source files
 ↓
Landing
 ↓
Orchestration (Airflow)
 ↓
Transformations / dbt + SQL
 ↓
Curated analytics
 ↓
Tests / quality
 ↓
Streamlit analytics
```

Describe only what the repository actually implements. Distinguish the current project from how you would productionize it in Snowflake/Fabric.

## Why the project is valuable for this interview
It bridges SQL, ETL/ELT, orchestration, dbt, testing, documentation and analytics—the same concepts emphasized by the training track.

## Questions to prepare
- Why Airflow?
- Why dbt?
- Where does SQL run?
- What is the grain of deliveries?
- How would you model batting/bowling facts and dimensions?
- How do you deduplicate deliveries?
- How do you handle late or corrected match data?
- How do you make the DAG idempotent?
- What tests protect data quality?
- How would you migrate this architecture to Snowflake?
- How would you rebuild it in Fabric OneLake/Lakehouse?

## Scaling story
```text
Landing → Bronze
Bronze → Silver with Spark/dbt
Silver → Gold dimensional model
Gold → Snowflake/Fabric Warehouse or semantic layer
Gold → Power BI / Streamlit
```
Discuss partitioning, incremental processing, schema evolution, monitoring and security as production enhancements, not as claims about the current repository.
