# Airflow Core Interview Notes

## What is Airflow?
An orchestration platform for defining, scheduling and monitoring workflows as code.

## DAG
A Directed Acyclic Graph describes task dependencies. A DAG should not contain cycles.

## Task / operator
A task is a unit of work. An operator is a reusable task implementation/template for a kind of work.

## Scheduler / worker / executor
- Scheduler decides what is ready to run.
- Executor determines how task execution is managed.
- Worker runs task work in executor setups that use workers.

## Retries
Retries address transient failures. Configure retry count and delay carefully; retries do not fix deterministic data-quality or logic errors.

## Idempotency
A retried task should not corrupt results or duplicate data. Use stable keys, upserts, checkpoints and atomic/transactional patterns where supported.

## XCom
Small pieces of task metadata can be exchanged between tasks. Do not use XCom as a substitute for a data warehouse or large-file storage.

## Variables / Connections
Variables store configuration-like values; Connections store reusable connection information. Follow organizational secret-management practices.

## Catchup / backfill
Catchup controls whether missed scheduled intervals are created when a DAG becomes active. Backfill intentionally runs historical intervals.

## Interview scenario
A daily ingestion DAG failed after loading raw data but before the curated merge. On retry, the target must not duplicate rows. Explain idempotent merge keys, run metadata and where the checkpoint/watermark is updated.

## Cricket project connection
Use your Cricket project to explain why orchestration is separate from SQL/dbt transformations and how tests can run as pipeline gates.
