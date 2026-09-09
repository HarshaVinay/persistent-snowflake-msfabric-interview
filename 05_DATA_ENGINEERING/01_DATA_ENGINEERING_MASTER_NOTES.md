# Data Engineering Master Notes

## Curriculum coverage
Cloud data stores, structured/semi-structured/unstructured data, OLTP/OLAP, DWH, lake, ODS, data mart, cleansing, denormalization, conceptual/logical/physical modeling, dimensional modeling, cloud warehouses, star/snowflake schema, SCD, ETL/ELT.

## OLTP vs OLAP
OLTP: operational transactions, frequent small writes, normalized models, strict transactional needs.
OLAP: analytical scans/aggregations, historical data, denormalized/star-oriented models.

## Lake vs Warehouse vs Lakehouse
- Data lake: broad, low-cost storage for raw and varied data.
- Warehouse: curated, structured analytical data with SQL-centric workloads.
- Lakehouse: combines lake storage flexibility with table/transaction/analytics capabilities.

## ETL vs ELT
ETL transforms before loading into the target.
ELT loads first and transforms in the target compute engine. ELT is natural for cloud warehouses such as Snowflake because storage and compute are separated.

## Dimensional modeling
Define the **grain first**. Then identify dimensions and measurable facts.

Example sales model:
```text
fact_sales
 - sales_key
 - date_key
 - customer_key
 - product_key
 - quantity
 - sales_amount

Dimensions: dim_date, dim_customer, dim_product
```

## SCD
Type 1 = overwrite current value.
Type 2 = preserve history with a new version, effective dates/current flag or equivalent.

## Incremental loading
Use a reliable watermark/CDC key, process only new or changed records, maintain idempotency and handle late-arriving data.

## Data quality
Validate schema, required columns, null rates, duplicates, domain/range rules, referential integrity, freshness and row-count anomalies.

## Architecture interview pattern
```text
Source → Ingestion → Raw/Landing → Transform → Curated → Serving → BI
```
Then discuss retries, idempotency, monitoring, security and cost.

## Persistent relevance
Recent Persistent reports repeatedly involve dimensional modeling, ETL/cloud architecture, SCD2, Medallion architecture, schema evolution and pipeline troubleshooting.

## P0
ETL/ELT, lake/warehouse/lakehouse, grain, facts/dimensions, star schema, SCD2, CDC/incremental, data quality, idempotency.
