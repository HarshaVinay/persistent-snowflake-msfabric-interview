# Microsoft Fabric Interview Research — September 2026

## Evidence level
**A = official Microsoft documentation / current platform behavior**  
**B = reported Persistent interview pattern**  
**C = high-probability prediction for this curriculum**

## Why Fabric matters for this candidate
The curriculum explicitly includes Fabric introduction, workloads, OneLake, Lakehouse, Delta, Spark/PySpark, Medallion Architecture, Data Factory, batch/incremental ingestion, Warehouse, SQL endpoint/T-SQL, star schema, Power BI, governance, RLS/CLS, lineage, monitoring and CI/CD. Therefore Fabric is a **P0 curriculum domain**, even though the public Persistent interview reports I found are more heavily concentrated on SQL, Spark/PySpark, Snowflake and Azure/Databricks.

## Current platform facts
Microsoft describes OneLake as the unified logical data lake underpinning Fabric workloads. Data can enter OneLake through uploads, pipelines, dataflows, streaming, shortcuts or mirroring. citeturn1search1turn1search3

A Fabric Lakehouse combines lake-scale storage with Spark and SQL access. Current Microsoft documentation states that Lakehouse data uses Delta Lake and that a Lakehouse exposes a SQL analytics endpoint. citeturn1search0

Microsoft currently distinguishes Lakehouse and Warehouse mainly by workload and development style: Lakehouse is Spark-oriented and supports structured and unstructured data; Warehouse is T-SQL/SQL-first and is intended for structured analytical workloads. Both use OneLake and Delta storage. citeturn1search0turn1search1

Microsoft's current Fabric guidance describes Medallion Architecture as Bronze/raw, Silver/enriched and Gold/curated, with the goal of progressively improving data quality and usability. citeturn1search5

## P0 interview questions to master

### OneLake
1. What is OneLake?
2. Why does Fabric need OneLake?
3. How is OneLake different from ADLS conceptually?
4. What are OneLake shortcuts?
5. When would you use a shortcut instead of copying data?

### Lakehouse
6. What is a Fabric Lakehouse?
7. Lakehouse vs Warehouse?
8. What are Files and Tables in a Lakehouse?
9. Why Delta format?
10. What is the SQL analytics endpoint?
11. Can Spark and SQL access the same Lakehouse data?

### Warehouse
12. When would you choose Fabric Warehouse?
13. How does a Warehouse fit the Gold layer?
14. How would you model a star schema in Fabric?
15. Lakehouse SQL endpoint vs Warehouse?

### Medallion
16. Explain Bronze → Silver → Gold.
17. What belongs in Bronze?
18. What transformations belong in Silver?
19. Why should Gold be business-ready?
20. Can users access Silver directly?
21. How would you handle bad records between layers?

### Data Factory
22. How would you build a batch pipeline?
23. How would you implement incremental ingestion?
24. Copy Activity vs Dataflow Gen2?
25. How do parameters and schedules work conceptually?
26. How would you handle pipeline failure and restart?
27. How would you make ingestion idempotent?

### Power BI
28. How does Power BI connect to Fabric?
29. What is Direct Lake?
30. Direct Lake vs Import vs DirectQuery?
31. Where should business logic live: Gold tables or semantic model?

### Security
32. What is RLS?
33. What is CLS?
34. How would you protect PII?
35. Where should access control be enforced?

## Current Direct Lake nuance
Current Microsoft documentation distinguishes Direct Lake on OneLake from Direct Lake on SQL. Direct Lake on OneLake reads through OneLake and can use OneLake security; Direct Lake on SQL is useful where security rules are defined at the SQL analytics endpoint and may use DirectQuery fallback for unsupported cases. citeturn1search4turn1search6

For a fresher interview, do not over-focus on implementation edge cases. Know the conceptual distinction and be able to explain why Direct Lake can avoid traditional import-style copying into an in-memory model.

## Recommended architecture answer
A strong curriculum-aligned answer is:

`Source systems → Fabric Data Factory / ingestion → Bronze Lakehouse → PySpark transformations → Silver Lakehouse → Gold curated data → Fabric Warehouse or Gold Lakehouse → Power BI`

Then add:
- incremental processing
- data-quality checks
- schema evolution strategy
- retry/recovery
- RBAC/RLS/CLS
- monitoring and lineage
- CI/CD
- cost/performance considerations

## Persistent evidence connection
Recent Persistent Data Engineer reports repeatedly emphasize Medallion Architecture, Azure/ADF/Databricks, Spark/PySpark optimization, dimensional modeling and pipeline scenarios. These reports do **not** prove that the same interviewer will ask Fabric-specific questions, but they strongly support preparing the underlying architecture concepts. citeturn0search2turn0search3

## Important honesty rule
Do not claim production Fabric experience if your experience is training/lab based. A strong answer is:

> “I worked with Fabric as part of my Revature training. I understand the architecture and implemented the training exercises around OneLake, Lakehouse, PySpark, Medallion, pipelines, Warehouse and Power BI. I would apply the same principles in production, while following the project's governance and deployment standards.”

## Sources
- Microsoft Learn — Lakehouse overview: citeturn1search0
- Microsoft Learn — Fabric storage options: citeturn1search1
- Microsoft Learn — OneLake quickstart: citeturn1search3
- Microsoft Learn — Medallion Architecture: citeturn1search5
- Microsoft Learn — Direct Lake security: citeturn1search4
- Microsoft Learn — Direct Lake development: citeturn1search6
- Persistent interview evidence: citeturn0search2turn0search3
