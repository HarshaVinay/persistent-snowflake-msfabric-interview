# Airflow Interview Core

## Mental model
DAG defines dependencies. Scheduler decides runnable task instances. Executor determines execution mechanism. Workers run tasks. Metadata database stores orchestration state. Operators describe work.

## Must know
DAG, task, operator, task instance, DAG run, scheduler, executor, worker, XCom, variables, connections, hooks, sensors, retries, trigger rules, catchup and backfill.

## Reliability
Retries should address transient failures; tasks should be idempotent. Use sensible timeouts, alerts, dependency rules and rerun-safe outputs.

## Databricks integration
Airflow can orchestrate a Databricks job while Databricks/Spark performs distributed processing.

## Interview note
Airflow is project/training support for this track, not one of the strongest directly reported Persistent fresher topics. Prioritize SQL/Spark/Snowflake first.