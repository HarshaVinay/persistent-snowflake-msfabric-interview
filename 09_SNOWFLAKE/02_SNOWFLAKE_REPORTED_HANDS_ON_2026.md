# Snowflake — Reported Persistent Hands-on Questions 2026

## Evidence level

The questions in this file come from recent candidate-reported Persistent Data Engineer interviews. They are not guarantees for your specific panel, but they are high-value because they overlap your Snowflake_MSFabric curriculum closely.

## 1. External stages

### Question
How do you read data from an external stage?

Know the distinction between:
- external stage;
- internal stage;
- stage/file path;
- storage integration/credentials at a conceptual level;
- file format.

A recent Persistent interview report explicitly included reading from an external stage. citeturn1search12

---

## 2. File formats

### Question
How do you define a CSV file format?

Know:
- type;
- field delimiter;
- header handling;
- null handling;
- compression;
- common file-format options.

A recent Persistent interview report explicitly included creating a file format. citeturn1search12

---

## 3. COPY

### Question
How do you load staged files into a Snowflake table?

Know the conceptual flow:

**source storage → stage → file format → COPY INTO → target table**

A recent Persistent report explicitly tested COPY. citeturn1search12

---

## 4. MERGE

### Question
How do you perform insert + update/upsert in Snowflake?

Know:

```sql
MERGE INTO target t
USING source s
ON t.id = s.id
WHEN MATCHED THEN
  UPDATE SET t.name = s.name
WHEN NOT MATCHED THEN
  INSERT (id, name)
  VALUES (s.id, s.name);
```

Be able to explain why MERGE is useful for incremental/CDC pipelines.

MERGE was explicitly reported in a recent Persistent interview. citeturn1search12

---

## 5. QUALIFY

### Question
How do you deduplicate rows in Snowflake?

```sql
SELECT *
FROM table_name
QUALIFY ROW_NUMBER() OVER (
  PARTITION BY id
  ORDER BY updated_date DESC
) = 1;
```

Know why `QUALIFY` is convenient: it filters on window-function results without requiring another outer query.

This exact style was reported in a recent Persistent Snowflake interview. citeturn1search12

---

## 6. Streams / CDC

### Question
What are Snowflake Streams and why would you use them?

Answer structure:

- A stream records change information for a table/view.
- It helps identify inserted/updated/deleted changes.
- It can feed incremental processing.
- A downstream task/procedure/dbt process can consume those changes.
- The design must account for consumption semantics, transaction boundaries and failure/retry behavior.

Streams/CDC were explicitly reported in the recent Persistent interview. citeturn1search12

---

## 7. Zero-copy cloning

A Persistent Data Engineer interview report explicitly identifies zero-copy cloning together with SQL window functions and Snowflake/PySpark. citeturn0search3

Know:
- what a clone is;
- why it is fast/space-efficient initially;
- how copy-on-write behavior relates to storage;
- practical uses such as development/testing/safe experimentation;
- limitations and governance considerations.

---

## 8. Snowflake performance

Your curriculum contains micro-partitions, pruning, clustering, statistics, cache layers, warehouse scaling, multi-cluster warehouses, profiling and cost optimization.

Prepare a structured answer:

1. inspect Query Profile;
2. identify scan/join/spill/queue bottleneck;
3. verify partition pruning;
4. reduce unnecessary columns/rows;
5. evaluate clustering only when justified;
6. evaluate warehouse size/concurrency;
7. understand cache behavior;
8. compare runtime against cost.

Do not answer “increase warehouse size” as the universal solution.

---

## 9. High-priority Snowflake drill

You should be able to answer without notes:

1. What is a virtual warehouse?
2. Storage vs compute?
3. What is a micro-partition?
4. What is pruning?
5. What is clustering?
6. Internal vs external stage?
7. File format?
8. COPY INTO?
9. MERGE?
10. QUALIFY?
11. VARIANT?
12. FLATTEN?
13. Time Travel?
14. Fail-safe?
15. Zero-copy cloning?
16. Streams?
17. Tasks?
18. RBAC?
19. masking/RLS?
20. Snowpark?
21. Query Profile?
22. result cache vs warehouse cache?
23. warehouse sizing?
24. multi-cluster warehouse?
25. cost optimization?

## Evidence note

Items 1–7 and Streams/CDC above have direct recent interview evidence where noted. The rest are curriculum-driven high-priority preparation, not claims that each exact question was asked in a Persistent interview.
