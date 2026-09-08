# Project 2 — Cricket Analytics Data Engineering Defence

## Verified repository structure
The repository includes `airflow`, `cricket_dbt`, `landing`, `sql`, `tests`, `docs`, and `streamlit_app`, making it a strong end-to-end data-engineering example. fileciteturn8file0L1-L5

## Interview story
Sources → landing → ingestion/validation → transformation → dbt models → orchestration → tests → analytics SQL → serving/visualization.

## Questions
- Why separate landing from curated data?
- Why Airflow?
- Why dbt?
- What is the DAG dependency graph?
- Where do data-quality tests run?
- How do you make reruns safe?
- How do you handle late/duplicate deliveries?
- How would you implement SCD2 if player/team attributes change?
- How would you move the pipeline to Snowflake?
- How would you implement it in Fabric?

## Strong architecture answer
Landing remains immutable/replayable; transformations create cleaned/conformed layers; dbt manages SQL transformations/tests/docs; Airflow controls scheduling/dependencies; curated models serve analytics. Then discuss monitoring, retry/idempotency and security.
