# Airflow Complete Master Notes

## Purpose
Airflow is an orchestration platform for scheduling and monitoring workflows expressed as DAGs.

## Core objects
- DAG: workflow definition.
- Task: one unit of work.
- Operator: template defining task behavior.
- DAG Run: one execution of a DAG.
- Task Instance: a task in a particular DAG run.
- Scheduler: schedules eligible tasks.
- Executor/worker architecture: runs tasks according to deployment configuration.
- XCom: small metadata/message passing between tasks; not a bulk data store.
- Connection: reusable external-system configuration.
- Variables: runtime configuration values.

## DAG example
```python
from airflow import DAG
from airflow.operators.python import PythonOperator

with DAG("daily_pipeline", schedule="@daily", start_date=..., catchup=False) as dag:
    extract = PythonOperator(task_id="extract", python_callable=extract_data)
    transform = PythonOperator(task_id="transform", python_callable=transform_data)
    extract >> transform
```

## Retries and failure handling
Configure retries/backoff for transient errors. Make tasks idempotent so retrying does not create duplicate outputs.

## Backfill / catchup
Backfill intentionally runs historical intervals. Catchup controls whether scheduled intervals created since the start date are automatically considered.

## Sensors
Wait for an external condition/event. Use carefully to avoid unnecessary worker/resource occupation; modern deferrable patterns can improve efficiency where supported.

## Airflow + data engineering
Typical pattern:
`source → Airflow orchestration → Spark/dbt/Snowflake → validation → serving`.
Airflow coordinates; it is not itself a distributed transformation engine.

## Project connection
Cricket Analytics contains an Airflow directory. Be ready to explain the DAG, task dependencies, retries, failure path, data dependencies and how the orchestrator interacts with SQL/dbt/processing.
