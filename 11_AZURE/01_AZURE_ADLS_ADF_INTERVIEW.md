# Azure / ADLS / ADF Interview Guide

## ADLS Gen2
Storage account → filesystem/container → directories/files. Hierarchical namespace enables directory/file semantics useful for analytics workloads.

## ADF concepts
Pipeline, activity, linked service, dataset, integration runtime, trigger, parameters, variables, expressions, copy activity, monitoring and failure handling.

## Incremental ingestion
Common pattern: identify watermark/last-modified value → extract only new/changed rows/files → load/merge → update watermark after successful processing.

## Reliability
Use retries, dependencies, idempotent writes, checkpoints/watermarks, quarantine for bad data, alerts and rerun-safe design.

## ADF + Databricks
ADF orchestrates movement/control flow; Databricks/Spark performs distributed transformations when appropriate. Pass parameters such as source path, date and target table.

## Security
Know Microsoft Entra ID, managed identity, RBAC, ACLs and the distinction between authentication and authorization.

## Interview prompts
- What are Integration Runtime types used for?
- How do you configure triggers?
- How do you copy many files in parallel?
- How do you make an ADF pipeline incremental?
- What happens when an activity fails?
- ADF vs Databricks: which does what?