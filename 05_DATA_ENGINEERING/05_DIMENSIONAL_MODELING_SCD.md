# Dimensional Modeling & SCD

## Fact vs dimension
**Fact** = measurable business event at a declared grain.
**Dimension** = descriptive context used to analyze facts.

Example:
```text
fact_sales
- sale_key
- customer_key
- product_key
- date_key
- quantity
- amount

DimCustomer
- customer_key
- customer_id
- name
- segment

DimProduct
- product_key
- product_id
- category
```

## Grain
Grain states exactly what one fact row represents.
Example: “one row per order line.”

Always define grain before selecting measures or joining dimensions.

## Star schema
Fact table in the center with denormalized dimensions around it. Simple analytics and predictable joins are the main strengths.

## Snowflake schema
Dimensions are normalized into additional related tables. It can reduce repeated attributes but introduces more joins.

## SCD Type 0
Never change the stored historical attribute.

## SCD Type 1
Overwrite the old value; no history retained.

## SCD Type 2
Preserve historical versions. Typical columns:
```text
surrogate_key
business_key
attribute...
effective_from
effective_to
is_current
```

Example change:
```text
Customer 101
IT → Finance
```
Type 2 results in two versions, one closed and one current.

## Type 2 process
1. Match incoming business key.
2. Detect whether tracked attributes changed.
3. Close current row (`is_current = false`, set effective_to).
4. Insert new version with new surrogate key and current flag.
5. Handle late-arriving data according to business rules.

## CDC and SCD
CDC identifies source changes. SCD describes how historical dimension state is stored. CDC can feed an SCD Type 2 pipeline, but the concepts are not identical.

## Interview questions
- What is grain?
- Why use surrogate keys?
- Star vs snowflake schema?
- Type 1 vs Type 2?
- Implement Type 2 using Spark/Snowflake/dbt.
- What happens if the same business key arrives twice?

## Project connection
For the Cricket project, identify the grain of match/delivery/player analysis before joining tables. For the Disaster project, protect the event-region grain from one-to-many joins and double counting.
