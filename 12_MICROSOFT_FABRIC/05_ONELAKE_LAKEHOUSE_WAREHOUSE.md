# Microsoft Fabric — OneLake, Lakehouse & Warehouse

## OneLake
Microsoft OneLake is the unified logical data lake for an organization in Fabric. Every Fabric tenant includes OneLake, and Fabric workloads use it as the central storage foundation.

Source: https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview

## Lakehouse
A Lakehouse combines lake-style storage with table/analytics capabilities. Fabric Lakehouse supports Files and Tables, with Delta as the table format in the standard workflow, and Spark/SQL access.

Current Microsoft documentation highlights one copy of data for engineering and analytics, Delta for ACID/schema enforcement/time travel, and Spark plus SQL access.

Source: https://learn.microsoft.com/en-us/fabric/data-engineering/lakehouse-overview

## Warehouse
Fabric Warehouse is optimized for SQL/T-SQL-centric analytical workloads and structured data. Use it when dimensional/relational analytical serving is the primary concern.

## Lakehouse vs Warehouse
| Dimension | Lakehouse | Warehouse |
|---|---|---|
| Primary tool | Spark/Python/SQL | T-SQL |
| Data shape | structured + unstructured | structured |
| Engineering | strong | moderate |
| BI serving | strong | strong |
| Typical use | engineering + lake analytics | SQL analytical serving |

Current Microsoft docs note that both use OneLake/Delta-based storage but target different development tools and workloads.

## SQL analytics endpoint
A Lakehouse exposes a SQL analytics endpoint for querying lakehouse tables with SQL. Treat it as a SQL access/serving surface, not as a separate copy of the underlying lakehouse data.

## Medallion
```text
Raw files
   ↓
Bronze
   ↓
Silver
   ↓
Gold
```

- Bronze: landed/raw data with traceability.
- Silver: cleaned, standardized, conformed data.
- Gold: business-ready facts/dimensions/aggregates.

## OneLake shortcuts
Shortcuts can provide access to data without creating another physical copy in the target location. Understand the governance/security implications before using them.

## Interview questions
1. What is OneLake?
2. Lakehouse vs Warehouse?
3. Why Delta?
4. What is the SQL analytics endpoint?
5. Explain Bronze/Silver/Gold.
6. Why not put everything directly in Gold?
7. How do you handle incremental data in the Lakehouse?
