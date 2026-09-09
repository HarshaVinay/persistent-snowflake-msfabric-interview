# Final Persistent Interview Master

## 1. Opening
### Tell me about yourself
Structure:
1. Present — Revature-trained Data Engineer.
2. Core stack — Python, SQL, Spark/PySpark, Snowflake, Fabric and data engineering.
3. Projects — Disaster Affected Region Tracker + Cricket Analytics.
4. Direction — interest in scalable analytics/data platforms.

Do not claim production experience you do not have.

## 2. Resume cross-examination
For every technology on the resume, answer:
- what it is;
- why it was used;
- what you personally did;
- one challenge;
- one optimization;
- one failure mode;
- one alternative.

## 3. Technical priority
P0: SQL, Python coding, Spark/PySpark, Snowflake, ETL/ELT, modeling/SCD, projects, Fabric/OneLake/Lakehouse, Azure/ADF.
P1: dbt, streaming, security/governance, Airflow, Delta, Power BI, Scala.

## 4. Rapid-fire questions
- SQL: third-highest salary? rank differences? latest row?
- Spark: narrow vs wide? shuffle? skew? repartition vs coalesce?
- PySpark: nulls? duplicate latest record? JSON flattening?
- Snowflake: warehouse? micro-partition? pruning? clustering? COPY? MERGE? QUALIFY? Streams? clone?
- Fabric: OneLake? Lakehouse vs Warehouse? Bronze/Silver/Gold? Direct Lake? Data Factory?
- Modeling: grain? fact vs dimension? SCD2?

## 5. Scenario round
Use:
**clarify → design → trade-offs → quality → security → failure → monitoring → cost.**

## 6. Project round
### Disaster
Be ready to explain ETL, Pandas cleaning, data-quality rules, relational schema, SQL analysis, grain issue, why MySQL, and scale-up design.

### Cricket
Be ready to explain landing, orchestration, Airflow, dbt, SQL, tests, documentation, analytics, failure handling, incremental processing and scale-up design.

## 7. Snowflake-to-Fabric comparison
Do not say they are the same product.
- Snowflake: warehouse/data platform centered on separate storage/compute and virtual warehouses.
- Fabric: integrated SaaS analytics platform centered on OneLake and multiple workloads.

## 8. If you don't know
Say:
“I haven't implemented that directly yet, but I understand the concept as follows…”
Then explain accurately. This is better than inventing experience.

## 9. Closing questions
Be ready to ask one intelligent question about the team's data platform, pipeline ownership, cloud stack or role expectations.

## 10. Final readiness standard
You should be able to answer common P0 questions verbally in under one minute, code standard SQL/Python/PySpark problems, and defend both projects under follow-up pressure.
