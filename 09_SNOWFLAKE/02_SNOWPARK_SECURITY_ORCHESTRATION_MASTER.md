# Snowpark + Snowflake Security + Orchestration Master Notes

## Snowpark
Snowpark lets developers use Python/Scala/Java APIs to build transformations that execute close to Snowflake data. Core concepts: Session, DataFrame operations, expressions, UDFs/procedures and avoiding unnecessary data movement.

### Interview question
"Why Snowpark instead of extracting data to Python?"
A strong answer: keep computation close to the data, reduce unnecessary movement, and use Snowflake compute/security where practical. Choose pure SQL when SQL is simpler and well supported.

## Authentication / access
Curriculum includes Python connector, REST APIs, key-pair and OAuth authentication, users/access control and RBAC.

Never put credentials directly in source code. Prefer supported secure credential/identity mechanisms and least privilege.

## RBAC mental model
```text
User → Role → Privileges → Objects
```
A role receives privileges on objects; users receive roles. Explain role hierarchy and least privilege at a conceptual level.

## Masking
Mask sensitive column values for users/roles who should not see raw values.

## Row-level security
Restrict which rows a user can see based on policy/business context.

## Audit/monitoring
Track access, query/workload behavior, failures and policy-relevant activity.

## Stored procedures / Tasks / Streams
Stored procedures contain procedural logic. Streams represent change information for supported objects. Tasks schedule/chain SQL or procedural work. Together they can support event-driven/incremental workflows.

## Security scenario
"Finance users may see all data, regional users only their region, and PII should be masked."
Answer: RBAC for privileges; row access policy for row restriction; masking policy for sensitive columns; audit/monitoring; test using representative roles.

## Priority
P1/P0 for Snowflake track security fundamentals; exact implementation syntax should follow current Snowflake documentation.
