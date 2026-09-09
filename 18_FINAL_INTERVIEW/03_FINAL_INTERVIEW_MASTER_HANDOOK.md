# Final Interview Master Handbook

## 1. Opening
Prepare a 60–90 second introduction that connects Revature training, Data Engineering specialization, the two projects, SQL/Python/PySpark/Snowflake/Fabric learning, and why the role is a fit.

## 2. Resume cross-examination
For every listed technology, know:
- what it is;
- where you used/studied it;
- why it was chosen;
- one implementation example;
- one limitation/trade-off.

Never claim production experience that the projects do not support.

## 3. Technical P0
### SQL
Window functions, joins, CTE/subqueries, duplicate/latest-row logic, employee-manager, aggregations, NULLs, query optimization.

### Python
Data structures, functions, OOP, exceptions, JSON/files, Pandas and coding.

### Spark/PySpark
Architecture, lazy evaluation, transformations/actions, narrow/wide, shuffle, partitions, joins, skew, repartition/coalesce, caching, AQE, JSON, windows, schema evolution, optimization.

### Data engineering
ETL/ELT, lake/warehouse/lakehouse, grain, facts/dimensions, star schema, SCD2, CDC, incremental, idempotency, quality.

### Snowflake
Architecture, warehouse, stage/COPY, file formats, micro-partitions, pruning, clustering, performance, semi-structured data, MERGE, QUALIFY, Streams, Time Travel, Fail-safe, cloning, RBAC, masking/RLS, Snowpark.

### Fabric
OneLake, Lakehouse, Warehouse, Delta, Spark/PySpark, Medallion, Data Factory, Copy Activity, incremental loading, SQL endpoint/T-SQL, star schema, Power BI, Direct Lake, governance/lineage/CI-CD.

## 4. Project deep dive
### Disaster
Be able to explain source → Pandas ETL → cleaning → MySQL → SQL → visuals; defend data-quality and grain decisions; explain how you would scale to Spark/Snowflake/Fabric.

### Cricket
Explain landing → orchestration → SQL/dbt/tests → analytics; know the grain of teams/players/matches/deliveries; explain idempotency, testing, incremental processing and how you would productionize on Snowflake/Fabric.

## 5. Scenario round
Use:
**Clarify → Design → Implement → Validate → Secure → Recover → Monitor → Optimize.**

## 6. Behavioral
Prepare STAR stories for:
- difficult problem;
- debugging/failure;
- disagreement/teamwork;
- learning a new tool;
- deadline pressure;
- explaining technical work simply.

## 7. When you do not know
Use: "I have studied the concept, but I have not implemented that in production. My understanding is..., and I would verify the platform-specific behavior before changing a production system."

## 8. Final readiness standard
You should solve common SQL/Python/PySpark questions without assistance, explain the end-to-end pipeline, defend both projects and answer why/why-not questions for major architectural choices.

## Evidence note
Current public Persistent interview guides report online assessment + technical interview(s) + HR as a common pattern, but actual loops can vary by assignment and level. Use the repository's evidence labels rather than assuming one fixed format.
