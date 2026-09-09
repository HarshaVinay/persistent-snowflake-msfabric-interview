# Snowflake Complete Master Notes

## 1. Architecture
Snowflake separates storage and compute. Data is stored in Snowflake-managed storage; virtual warehouses provide compute; cloud services handle metadata, optimization, security and coordination.

## 2. Virtual warehouses
A warehouse is a compute cluster used for queries, DML and data loading. Size controls available compute. Auto-suspend/resume can reduce idle cost. Multi-cluster warehouses can provide additional clusters for concurrency.

## 3. Micro-partitions
Snowflake automatically divides table data into contiguous micro-partitions. Current Snowflake documentation states each contains about 50–500 MB of uncompressed data. They are columnar and compressed, and Snowflake stores metadata such as value ranges and distinct-value information. citeturn756531search0

## 4. Pruning
Query pruning skips micro-partitions that cannot satisfy predicates. Better data organization can improve pruning. Not every predicate expression is equally prune-friendly. citeturn756531search0

## 5. Clustering
Clustering can improve pruning for large tables with important recurring filter/join patterns when natural organization is insufficient. It adds maintenance/compute considerations, so it should be justified by workload benefit. citeturn756531search0

## 6. Loading
Mental flow:
`cloud/local files → stage → file format → COPY INTO → Snowflake table`.

Know user/table/named/internal/external stage concepts and `COPY INTO` error-handling options.

```sql
COPY INTO sales
FROM @sales_stage
FILE_FORMAT = (TYPE = CSV)
ON_ERROR = 'CONTINUE';
```

## 7. MERGE
Used for deterministic upsert patterns.

```sql
MERGE INTO target t
USING source s
ON t.id = s.id
WHEN MATCHED THEN UPDATE SET t.amount = s.amount
WHEN NOT MATCHED THEN INSERT (id, amount) VALUES (s.id, s.amount);
```

## 8. QUALIFY
Filters results after window functions without an extra nesting layer.

```sql
SELECT *, ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY updated_at DESC) rn
FROM customer_events
QUALIFY rn = 1;
```

## 9. Semi-structured data
Use `VARIANT` for flexible JSON-like data and functions such as `FLATTEN` to expand arrays/objects. Know path navigation and explicit casting.

## 10. Tables and views
Know permanent, temporary, transient and external tables, plus views and materialized views. Exact feature behavior should be checked against current Snowflake documentation.

## 11. Time Travel, Fail-safe, cloning
Time Travel provides historical access/recovery within configured retention. Fail-safe is a Snowflake-managed recovery period after Time Travel. Zero-copy cloning creates a logical clone without initially making a full physical copy; changed data is stored separately as needed.

## 12. Streams and tasks
Streams expose change information for table data; tasks schedule/automate SQL workflows. Together they can implement incremental pipelines, but production design must include idempotency, monitoring and failure handling.

## 13. Performance
Use Query Profile. Identify whether the bottleneck is scan/pruning, join, aggregation, spill, queueing or compute. Reduce data scanned, optimize joins, use clustering only when justified, size warehouses appropriately and exploit caching where applicable.

## 14. Cache layers
Know result caching versus warehouse/local data caching at a conceptual level. Do not assume every rerun benefits equally; query text/result eligibility and workload context matter.

## 15. Cost optimization
- Auto-suspend idle warehouses.
- Right-size warehouses.
- Separate workloads.
- Reduce unnecessary scans.
- Use incremental loads.
- Avoid gratuitous clustering.
- Monitor warehouse/query spend.

## 16. Security
Users receive privileges through roles. Know RBAC, masking policies, row access policies and audit/monitoring.

## 17. Snowpark
Snowpark lets developers execute data transformations close to the data using language APIs such as Python. Prefer native platform operations when they are simpler and better optimized.

## 18. Persistent P0
Know especially:
- warehouse vs storage
- micro-partitions
- pruning
- clustering
- stages/file formats/COPY
- MERGE
- QUALIFY
- Streams/CDC
- Time Travel/Fail-safe
- Zero-copy cloning
- performance troubleshooting
- security basics
