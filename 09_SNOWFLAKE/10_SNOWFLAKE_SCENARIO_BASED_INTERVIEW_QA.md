# Snowflake — Scenario-Based Interview Questions & Model Answers

**Track:** Revature → Persistent Snowflake_MSFabric  
**Audience:** Fresher / client technical interview  
**Use with:** `09_SNOWFLAKE/09_SNOWFLAKE_TOP_50_INTERVIEW_QA.md`

> These are **scenario questions**, not claims that every question was directly asked at Persistent. They are designed from the user's curriculum, uploaded Snowflake handbook, and recurring Persistent data-engineering interview patterns.

---

## Scenario 1 — A Snowflake query is slow

### Question
A dashboard query that used to finish in 20 seconds now takes 5 minutes. What do you do?

### Model answer
“I would not immediately increase the warehouse. First I would inspect query history and the Query Profile to identify whether the bottleneck is scanning, joins, spilling, warehouse queuing or compute. Then I would check whether predicates are pruning micro-partitions, whether the query reads unnecessary columns, whether joins are causing excessive work, and whether the workload has changed. Depending on the root cause I could improve filtering/projection, review clustering, resize the warehouse, isolate concurrency or redesign the query. Finally I would compare both runtime and cost before and after the change.”

### Follow-ups
- What does pruning mean?
- What does Query Profile tell you?
- When is clustering justified?
- Why can a bigger warehouse fail to solve the problem?

---

## Scenario 2 — Large table filtered by date

### Question
A 10-billion-row `SALES` table is mostly queried by `ORDER_DATE`. How would you improve it?

### Model answer
“First I would verify actual query patterns and pruning. If the table is large and the date filters are selective, I would consider clustering on `ORDER_DATE` or an appropriate expression if it materially improves micro-partition organization. I would validate clustering benefit using query performance and pruning metrics rather than assuming clustering is always necessary.”

---

## Scenario 3 — You have 100 CSV files to load

### Question
How would you load them into Snowflake?

### Model answer
“I would put the files in an appropriate internal or external stage, define a reusable file format, and use `COPY INTO`. I would configure file selection and error handling as needed.”

```sql
COPY INTO SALES
FROM @sales_stage
FILE_FORMAT = (TYPE = CSV)
PATTERN = '.*sales_.*[.]csv'
ON_ERROR = 'CONTINUE';
```

---

## Scenario 4 — Files have headers and bad records

### Question
The CSV files have headers and occasionally contain invalid rows. What would you configure?

### Model answer
“I would define a CSV file format with `SKIP_HEADER = 1`, then choose `ON_ERROR` according to the data-quality requirement. If bad records must not stop the entire load, I might use `CONTINUE`, but I would also capture/review the rejected records rather than silently losing them.”

```sql
CREATE FILE FORMAT sales_csv
  TYPE = CSV
  SKIP_HEADER = 1;
```

---

## Scenario 5 — The source sends the same file twice

### Question
How do you prevent duplicate ingestion?

### Model answer
“I would avoid relying only on the target table to detect duplicates. I would use Snowflake's load history/file metadata behavior where applicable, plus pipeline-level idempotency. For row-level duplicates I would define a business key and deduplicate the data before or during the merge into the target.”

### Strong follow-up
“How would you design it so a pipeline can safely run again?”

Answer: make the processing **idempotent**—the same input should not create additional incorrect business rows if processed again.

---

## Scenario 6 — Incremental upsert

### Question
Every day you receive changed customer records. How would you load them?

### Model answer
“I would land the source data in a stage/table, identify the business key and changed records, then use `MERGE` to update matches and insert new records. If the source has reliable timestamps or CDC metadata, I would process incrementally rather than scan the entire source.”

```sql
MERGE INTO CUSTOMER_TGT t
USING CUSTOMER_STAGE s
ON t.CUSTOMER_ID = s.CUSTOMER_ID
WHEN MATCHED THEN
  UPDATE SET
    t.NAME = s.NAME,
    t.EMAIL = s.EMAIL,
    t.UPDATED_AT = s.UPDATED_AT
WHEN NOT MATCHED THEN
  INSERT (CUSTOMER_ID, NAME, EMAIL, UPDATED_AT)
  VALUES (s.CUSTOMER_ID, s.NAME, s.EMAIL, s.UPDATED_AT);
```

---

## Scenario 7 — Latest record per customer

### Question
A table contains multiple versions of each customer. Return only the latest record.

### Model answer
Use `ROW_NUMBER()` partitioned by customer and order descending by update timestamp. In Snowflake, `QUALIFY` is convenient for filtering the window result.

```sql
SELECT *
FROM CUSTOMER_HISTORY
QUALIFY ROW_NUMBER() OVER (
    PARTITION BY CUSTOMER_ID
    ORDER BY UPDATED_AT DESC
) = 1;
```

---

## Scenario 8 — Detect changes continuously

### Question
You need to process changed rows from a Snowflake table without repeatedly scanning the whole table.

### Model answer
“I would consider a Stream to capture changes and a Task to run downstream processing. The task can apply the changed rows to a target using `MERGE` or another transformation.”

```text
Source table
   ↓
Stream
   ↓
Task
   ↓
Transform / MERGE
   ↓
Target
```

---

## Scenario 9 — You need scheduled automation

### Question
A transformation must run every hour. What Snowflake feature could you use?

### Model answer
“A Snowflake Task can schedule or trigger the processing. For event-driven incremental processing I could combine a Stream with a Task.”

---

## Scenario 10 — Developer wants a production copy for testing

### Question
They need to test schema/data changes without changing production. What Snowflake feature would you consider?

### Model answer
“I would consider zero-copy cloning for an appropriate supported object. It provides a fast logical copy without immediately duplicating the full underlying storage. I would still apply correct access controls and be clear about what changes are independent after the clone is created.”

---

## Scenario 11 — Someone deleted important rows

### Question
What would you investigate first?

### Model answer
“I would determine when the deletion happened and whether the object/data is still within the applicable Time Travel retention period. If so, I could use Time Travel for historical inspection or recovery where supported. I would not describe Fail-safe as the normal operational recovery mechanism.”

---

## Scenario 12 — The business wants a historical report

### Question
They want to know what a table looked like at an earlier point in time.

### Model answer
“I would evaluate Snowflake Time Travel and use an appropriate historical query or recovery workflow within the retention period. The exact syntax would depend on whether the requirement is time-based or statement-based.”

---

## Scenario 13 — A business analyst sends huge JSON documents

### Question
How would you store and query them?

### Model answer
“I would consider storing the semi-structured payload in a `VARIANT` column when that fits the access pattern. I would then navigate JSON paths for scalar attributes and use `FLATTEN` for arrays or nested repeated structures.”

```sql
CREATE TABLE EVENTS (
    RAW_DATA VARIANT
);
```

---

## Scenario 14 — Nested JSON array needs to become rows

### Question
Each event contains an array of orders. How do you convert each order into a row?

### Model answer
“I would use `LATERAL FLATTEN` on the array path, then extract fields from the flattened value.”

Conceptually:

```sql
SELECT
    e.RAW_DATA:id::STRING AS EVENT_ID,
    f.value:order_id::STRING AS ORDER_ID
FROM EVENTS e,
LATERAL FLATTEN(input => e.RAW_DATA:orders) f;
```

---

## Scenario 15 — ETL and BI are competing for compute

### Question
Your ETL jobs run at the same time as BI dashboards. What would you consider?

### Model answer
“I would consider separate Virtual Warehouses for independent workloads so ETL and BI have isolated compute. I would also evaluate warehouse sizing, auto-suspend/resume, workload scheduling and concurrency. I would avoid assuming that simply adding compute is the only solution.”

---

## Scenario 16 — Many concurrent BI users

### Question
The main problem is high query concurrency. What Snowflake feature might help?

### Model answer
“I would evaluate a multi-cluster warehouse if the workload needs additional clusters to handle concurrency. I would distinguish this from scaling the size of a single warehouse for additional compute on an individual workload.”

---

## Scenario 17 — Snowflake costs suddenly increase

### Question
How would you investigate?

### Model answer
“I would review warehouse usage, query history and workload timing. I would check for warehouses running continuously, oversized warehouses, unexpected concurrency, inefficient queries, repeated full scans or unnecessary clustering. Then I would apply right-sizing, auto-suspend/resume and query/storage optimizations based on evidence.”

---

## Scenario 18 — Developers are downloading Snowflake data into Python

### Question
The data is huge and they are moving it to local Python for transformations. What would you suggest?

### Model answer
“If the transformation can be expressed with Snowpark, I would consider processing closer to the Snowflake data using Snowpark DataFrames. That can reduce unnecessary movement of large datasets from Snowflake to an external Python process.”

The uploaded Snowpark material uses exactly this comparison: traditional data movement versus processing with Snowpark in Snowflake. fileciteturn1file5L722-L734

---

## Scenario 19 — SQL is awkward for custom business logic

### Question
What would you use?

### Model answer
“I would first see whether standard SQL is sufficient. For reusable value-level logic, a UDF may fit. For multi-step procedural workflows, a Stored Procedure may be more appropriate. If Python-style DataFrame logic is useful and should execute in Snowflake, Snowpark is another option.”

---

## Scenario 20 — Protect sensitive customer data

### Question
The table contains PII such as email, phone and government identifiers. What should you consider?

### Model answer
“I would use RBAC with least privilege, restrict who can query sensitive columns, and consider masking policies and row-access policies where appropriate. I would also audit access and separate developer/analyst roles. Security should be applied at the data-platform layer rather than relying only on application code.”

---

## Scenario 21 — A user should only see rows for their region

### Question
How would you approach it?

### Model answer
“I would consider a row-access policy driven by user role or entitlement information so the query automatically returns only the rows the user is authorized to see.”

---

## Scenario 22 — Developer should see masked email but authorized users need the real value

### Question
What Snowflake feature is appropriate?

### Model answer
“I would consider dynamic data masking with role-aware masking logic. The policy can return a masked representation for ordinary roles and the unmasked value for specifically authorized roles, according to the security design.”

---

## Scenario 23 — A table is huge but clustering seems expensive

### Question
Would you still cluster it?

### Model answer
“Not automatically. I would first establish the workload's filtering patterns and measure whether better clustering meaningfully improves pruning and performance. If the benefit is small compared with maintenance cost, I would leave the table without explicit clustering.”

---

## Scenario 24 — Loading succeeds for some files and fails for others

### Question
How do you handle it operationally?

### Model answer
“I would configure appropriate `ON_ERROR` behavior, capture load results and failed-file information, quarantine or correct bad inputs, and make the pipeline restartable. I would not hide bad records just to make a job appear successful.”

---

## Scenario 25 — Production pipeline failed after loading the stage but before merge

### Question
How should the rerun behave?

### Model answer
“I would design the pipeline to be restartable and idempotent. The stage should remain available as the source of truth for the batch, and the target merge should be keyed on business identifiers so rerunning the same input does not create duplicate business records. I would also make each processing step observable.”

---

# Interview answer formula for Snowflake scenarios

Use this sequence:

```text
1. Clarify the problem
2. Identify data volume and workload pattern
3. Inspect evidence/metadata/logs
4. Choose the Snowflake feature that fits
5. Explain why
6. Mention data quality/failure handling
7. Mention security where relevant
8. Mention performance/cost trade-off
9. Validate the result
```

## Example

**Interviewer:** “The query is slow. What do you do?”

**Weak:** “Increase the warehouse.”

**Strong:** “First I would inspect Query Profile and query history to identify the bottleneck. I would check scanning and pruning, joins, spill, concurrency and warehouse queuing. Then I would optimize the query or storage organization based on the root cause and resize the warehouse only if compute capacity is actually the bottleneck. Finally I would compare both runtime and cost.”

---

# 10 scenarios to practice aloud without notes

1. Slow query on a huge fact table.
2. Duplicate source files.
3. Incremental customer upsert.
4. CDC with Stream + Task.
5. Nested JSON array.
6. ETL and BI contention.
7. Cost spike.
8. PII masking.
9. Failed pipeline restart.
10. Snowpark vs external Python processing.

### Final reminder

For Persistent, do not answer with only feature definitions. State the **problem → diagnosis → chosen feature → trade-off → validation**. Recent Persistent Data Engineer interview material emphasizes real-world optimization, Snowflake, PySpark, SQL and architecture rather than definitions alone. citeturn353424search1
