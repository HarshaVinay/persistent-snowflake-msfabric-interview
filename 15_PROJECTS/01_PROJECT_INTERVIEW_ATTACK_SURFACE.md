# Project Interview Attack Surface

## Why this file exists

Persistent interviews repeatedly include project deep dives. The interviewer can use a project to test whether the candidate genuinely understands SQL, PySpark, ETL, modeling, data quality, cloud architecture and trade-offs.

## Project 1 — Disaster Affected Region Tracker

### Must explain
- problem statement and business goal;
- source data and data grain;
- ingestion and transformation sequence;
- cleaning and missing-value handling;
- duplicate handling;
- schema/model;
- SQL analysis;
- output/visualization;
- validation;
- limitations;
- how the design would scale.

### Attack questions
1. What was the grain of the source data?
2. How did you detect duplicates?
3. How did you handle missing values?
4. Why did you choose Pandas/MySQL for this project?
5. What happens if the data volume becomes 100x larger?
6. How would you redesign it with Spark?
7. How would you implement Bronze/Silver/Gold?
8. How would you load it into Snowflake?
9. What would be fact and dimension tables?
10. How would you implement incremental ingestion?
11. How would you test data quality?
12. What would you monitor in production?

### Critical honesty rule
Only describe implementation as completed if it was actually implemented. For improvements, use wording such as: "For the original project I used X. If I scaled it, I would use Y because..."

## Project 2 — Cricket Analytics Data Engineering

### Repository signals
The project repository contains areas for `landing`, `airflow`, `cricket_dbt`, `sql`, `tests`, `docs`, and `streamlit_app`.

### Must explain
- source files and landing design;
- ingestion/orchestration;
- transformations;
- dbt models and tests;
- SQL analytics;
- data-quality approach;
- failure/retry handling;
- serving/visualization;
- project architecture;
- why each technology was selected.

### Attack questions
1. Walk me through the pipeline end to end.
2. Why did you use Airflow?
3. What is a DAG?
4. How do you prevent duplicate processing?
5. What happens when a task fails?
6. Why dbt?
7. What is the difference between a dbt source, seed and model?
8. Which materialization would you use and why?
9. How would you implement an incremental model?
10. How would you implement SCD Type 2?
11. How would you migrate this project to Snowflake?
12. How would you rebuild it in Fabric?
13. What becomes Bronze, Silver and Gold?
14. Where would data quality tests run?
15. How would you handle a new source column?
16. How would you monitor freshness and failures?
17. How would you optimize a slow transformation?
18. What would you change if the data grew from MB/GB to TB?

## Cross-project comparison questions

- Why Pandas in one project and Spark in another?
- Why MySQL versus Snowflake?
- What is the difference between batch ETL and a production orchestration platform?
- Which project better demonstrates data engineering?
- What did you personally implement versus study?
- What was the hardest problem?
- What would you redesign today?

## Interview answer structure

Use:
**Context → Data → Architecture → Transformation → Quality → Failure handling → Performance → Security → Outcome → Improvement.**
