# Snowflake Security, Programming & Snowpark

## RBAC
Snowflake access control is role-based: privileges are granted to roles, and roles are assigned to users/other roles according to the account's design.

Core terms:
- user
- role
- privilege
- database/schema/object
- role hierarchy

## Masking vs row access
- Masking policies protect values in selected columns.
- Row access policies control which rows are visible.

## UDFs
A user-defined function encapsulates reusable logic and returns a value. Snowflake supports SQL and other language options subject to platform/runtime rules.

Use built-in functions first when they already express the logic; custom UDFs are for genuine business logic gaps.

## Stored procedures
Stored procedures execute procedural/business logic and can orchestrate multiple statements or operations.

## Snowpark
Snowpark provides language APIs, especially Python/Scala/Java, that let processing logic run close to Snowflake data rather than pulling large datasets to an external client.

Conceptually:
```text
Python logic
   ↓
Snowpark DataFrame
   ↓
Snowflake execution
   ↓
Data remains governed by Snowflake
```

## Snowpark vs traditional connector
A traditional Python connector commonly sends SQL and retrieves result data to the client. Snowpark is intended for expressing data-processing logic using DataFrame APIs that execute within Snowflake's environment.

## Security interview scenario
**Requirement:** analysts see all rows, but regional managers only see their region and sensitive salary columns are masked.

Answer:
- use role-based grants for objects;
- use row access policy for regional filtering;
- use masking policy for salary;
- verify role inheritance and least privilege;
- audit access and test both privileged and restricted roles.

Do not claim a policy runs “at ingestion”; distinguish access-time controls from pipeline-time transformations.
