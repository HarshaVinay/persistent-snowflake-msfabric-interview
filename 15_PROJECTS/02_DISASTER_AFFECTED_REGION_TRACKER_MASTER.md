# Project 1 — Disaster Affected Region Tracker Master Notes

## Repo
https://github.com/HarshaVinay/Disaster-Affected-Region-Tracker-Analysis

## One-line answer
"I built a small end-to-end data pipeline that ingests disaster-related CSV data, cleans and standardizes it with Pandas, loads curated relational data into MySQL, runs analytical SQL, and produces visualizations."

## Architecture
```text
CSV sources
 ↓
Pandas ETL
 ↓
clean datasets
 ↓
MySQL relational tables
 ↓
analytical SQL
 ↓
visualizations
```

## Data-quality work
Be ready to explain deduplication, date parsing, numeric conversion, missing-value handling and business rules. A good answer always explains why the chosen default was appropriate for the business meaning.

## Modeling/grain
The important interview issue is row grain. A region-name join can multiply records if the region table contains multiple rows for the same region name. State the grain before joining and validate row counts after joins.

## SQL analytics
Top affected regions, severity distribution, monthly disaster trends, economic loss vs affected population, and region-wise disaster frequency.

## Why this architecture?
For a supplied small dataset, Pandas + MySQL is simpler and sufficient. Do not claim Spark/Snowflake was required merely because this interview track teaches them.

## Scale-up answer
```text
Object storage / landing
 ↓
Spark/PySpark
 ↓
Bronze → Silver → Gold
 ↓
Snowflake or Fabric Warehouse/Lakehouse
 ↓
BI
```

## Likely attack questions
1. Why Pandas instead of Spark?
2. Why MySQL?
3. What was the grain?
4. Why median for missing population?
5. Why zero for missing impact?
6. How did you validate duplicates?
7. What happens at 100 GB/1 TB?
8. How would you add incremental loading?
9. How would you implement SCD2?
10. How would you monitor the pipeline?
