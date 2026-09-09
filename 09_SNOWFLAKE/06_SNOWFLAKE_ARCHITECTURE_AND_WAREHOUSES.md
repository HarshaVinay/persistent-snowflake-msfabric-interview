# Snowflake Architecture & Virtual Warehouses

## Mental model
Snowflake separates **storage** from **compute** and provides cloud services for metadata, optimization, security and coordination.

```text
                Snowflake
        ┌──────────┼──────────┐
        ↓          ↓          ↓
     Storage     Compute   Cloud Services
        │          │          │
  Micro-part.   Virtual    Metadata /
  compressed    Warehouse  optimization /
  columnar                 security
```

## Virtual warehouse
A virtual warehouse is a cluster of compute resources used for queries, DML and data loading/unloading work.

Warehouse size controls available compute/memory per cluster. Scaling up can help compute-heavy workloads; it does not fix every problem.

## Auto-suspend / auto-resume
- Auto-suspend stops idle compute after a configured interval.
- Auto-resume starts compute when work arrives.
These features can control cost for intermittent workloads.

## Multi-cluster warehouse
Multiple clusters can be used to handle concurrency. This addresses simultaneous demand rather than making one query inherently better optimized.

## Scaling up vs out
- Vertical scale: larger warehouse for more compute per query.
- Multi-cluster/horizontal: more clusters to support concurrency.

## Query queuing
When demand exceeds the currently available compute, queries may queue. A bigger warehouse may help in some cases, while multi-cluster can help concurrency. Inspect the workload before choosing.

## Cost discipline
1. Optimize unnecessary scans and joins.
2. Use appropriate warehouse size.
3. Use auto-suspend where suitable.
4. Separate workloads when contention matters.
5. Use multi-cluster when concurrency justifies it.
6. Monitor credits and query history.

## Interview question
**Does increasing warehouse size always improve performance?**
No. If the bottleneck is poor SQL, excessive data scanned, weak pruning, a bad join pattern, or another non-compute issue, a larger warehouse may add cost without fixing the root cause.
