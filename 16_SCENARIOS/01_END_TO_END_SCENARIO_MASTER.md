# End-to-End Scenario Master

## Scenario 1: Daily batch pipeline
Source → landing/raw → Bronze → Silver → Gold → Snowflake/Fabric Warehouse → Power BI.

## Scenario 2: Incremental pipeline
Identify watermark/CDC → ingest changes → deduplicate by business key + latest timestamp → merge/upsert → validate counts → advance watermark only after success.

## Scenario 3: Schema changes
Detect schema drift → classify compatible/breaking change → quarantine or evolve contract → update transformations/tests → replay affected data.

## Scenario 4: Failed pipeline
Preserve raw input → inspect failed activity/stage → fix root cause → rerun from safe checkpoint → reconcile counts and audit records → alert stakeholders.

## Scenario 5: Spark is slow
Spark UI → slow stage → shuffle/skew/partition analysis → join strategy → filtering/projection → partition sizing → AQE/cache where justified.

## Scenario 6: Snowflake query is slow
Query Profile → scan/pruning → joins/spills → warehouse queue/size → clustering only if justified → rewrite SQL → compare elapsed time and credits.

## Scenario 7: PII
Classify sensitive columns → least privilege/RBAC → masking → row-level restrictions where needed → encryption/secret management → audit access.

## Interview framework
**Requirements → grain → volume/SLA → ingestion → transformation → storage → serving → quality → reliability → security → monitoring → cost.**