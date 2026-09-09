# Cloud Data Architecture Master Notes

## Curriculum
Service types, IaaS/PaaS/SaaS, AWS/Azure/GCP overview, pricing, components, architecture, benefits, challenges, structured/semi-structured/unstructured data, file types, data stores, OLTP/OLAP, DWH/data lake, DWH architecture, ODS, data mart.

## IaaS/PaaS/SaaS
IaaS: infrastructure is managed by provider, user manages more of the software stack.
PaaS: provider manages platform/runtime; user focuses on applications/data.
SaaS: complete application delivered as a service.

## Data types
Structured → fixed schema/tabular.
Semi-structured → self-describing/nested such as JSON.
Unstructured → documents, images, audio and similar content.

## OLTP vs OLAP
```text
OLTP → operational transactions → frequent small reads/writes
OLAP → analytics → scans/joins/aggregations/history
```

## Data warehouse architecture
```text
Sources → ingestion → staging/raw → transformation → warehouse → marts/BI
```

## ODS
Operational Data Store is an integrated store useful for near-current operational reporting and intermediate integration workloads; exact architecture varies.

## Data mart
A subject-oriented analytical subset, often serving a business function such as finance or sales.

## Cost thinking
Cloud decisions balance compute, storage, data transfer, concurrency, availability, operational effort and workload variability.

## Interview question
"How would you choose a cloud data platform?"
Answer using requirements first: volume, latency/SLA, source types, transformation tools, security, concurrency, team skill, integration, recovery and cost—not brand preference.
