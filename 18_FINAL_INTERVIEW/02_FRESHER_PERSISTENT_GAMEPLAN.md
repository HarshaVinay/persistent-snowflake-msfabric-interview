# Fresher Persistent Final Interview Game Plan

## Goal
Convert Revature Persistent Snowflake_MSFabric training into interview-ready performance.

## Round mindset
The most relevant fresher evidence says the final Persistent stage can focus heavily on what was taught during Revature training, coding, SQL, technical discussion, resume and projects.

## The interviewer's likely decision questions
1. Does the candidate actually understand the training material?
2. Can the candidate write basic-to-intermediate code without heavy prompting?
3. Can the candidate solve SQL analytically?
4. Can the candidate explain a data pipeline end to end?
5. Does the candidate understand the tools named on the resume?
6. Can the candidate reason through failures and trade-offs?
7. Can the candidate communicate clearly and honestly?

## Answer strategy
### For a definition
Definition → why it exists → simple example → one trade-off.

### For coding
Restate → identify edge cases → write simple correct solution → test mentally → improve only if needed.

### For architecture
Requirements → source → ingestion → raw/Bronze → transformation/Silver → serving/Gold → warehouse/BI → quality → security → monitoring → recovery → cost.

### For project questions
Problem → data → architecture → your contribution → transformation → storage → validation → challenge → solution → result → what you would improve.

## P0 live-coding practice
### Python
- remove duplicates without set
- second highest value
- frequency count
- string/list manipulation
- basic functions and loops

### SQL
- second/third highest salary
- duplicates
- latest row per key
- employee vs manager
- top N per department
- RANK vs DENSE_RANK
- running total
- moving average

### PySpark
- create DataFrame
- null handling
- groupBy/count
- joins
- window functions
- nested JSON/explode
- deduplication
- write Parquet/Delta

### Snowflake
- create file format
- stage/query stage
- COPY INTO
- MERGE
- QUALIFY deduplication
- Streams concept

## Snowflake_MSFabric specialization questions
These are high-probability curriculum questions, not confirmed exact questions:
- What is a micro-partition?
- How does pruning work?
- What is clustering and when is it useful?
- Warehouse vs storage?
- What is Time Travel?
- Time Travel vs Fail-safe?
- What is zero-copy cloning?
- What is Snowpark?
- Lakehouse vs Warehouse in Fabric?
- What is OneLake?
- Explain Bronze/Silver/Gold.
- How would you build an incremental Fabric pipeline?
- What is Delta format?
- How does Power BI connect to Fabric data?
- How would you implement RLS?

## Project defense
### Disaster project
Be able to explain every transformation, join, data-cleaning decision, SQL analysis and limitation.

### Cricket project
Be able to explain landing, ingestion/orchestration, Airflow, dbt, SQL, tests, documentation and serving/analytics. Be explicit about what you personally implemented versus what you studied.

## If you do not know an answer
Use:
> "I have not implemented that directly yet, but based on my training I understand the concept as..."

Then explain the known part. Never invent production experience.

## Final rule
Strong fundamentals + clean reasoning + honest project ownership beats memorized advanced terminology.
