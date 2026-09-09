# Airflow Master Notes

## Scope
Airflow is supporting/project knowledge, not a core standalone item in the exact latest pasted curriculum. The Cricket project repository contains an `airflow` area, so prepare project-level understanding.

## Mental model
```text
DAG → tasks → dependencies → scheduler → executor/worker
```

A DAG defines workflow structure and dependencies. A task is a unit of work. Scheduler determines runnable tasks; executor/worker executes them according to deployment architecture.

## Core terms
DAG, DAG Run, Task, Operator, Task Instance, Scheduler, Executor, Worker, XCom, Variables, Connections, Hooks, Sensors, retries, catchup, backfill.

## Reliability
Use retries, sensible timeouts, idempotent tasks, clear dependencies and alerts. A retry-safe pipeline should not duplicate output.

## Incremental pipeline
Airflow should orchestrate rather than contain large data transformations. Trigger ingestion, Spark/dbt/Snowflake work, validate, publish watermark and alert on failure.

## Interview questions
- What is a DAG?
- Task vs operator?
- Scheduler vs executor?
- How do retries work conceptually?
- How do you make an Airflow pipeline idempotent?
- How would Airflow orchestrate a Snowflake/dbt pipeline?

## Project connection
Use Cricket Analytics to explain where Airflow sits in the architecture and which tasks it coordinates. Do not claim infrastructure ownership that the repository does not show.
