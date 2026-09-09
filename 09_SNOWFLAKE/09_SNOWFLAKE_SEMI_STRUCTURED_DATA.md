# Snowflake Semi-Structured Data

## Core types
Snowflake commonly uses `VARIANT` for semi-structured values. Related types include `OBJECT` and `ARRAY`.

## Why VARIANT?
It allows JSON-like hierarchical data to be stored and queried without forcing every nested attribute into a fixed relational schema immediately.

## Example
```sql
SELECT payload:user:id::NUMBER AS user_id,
       payload:event::STRING AS event_name
FROM raw_events;
```

The colon/path notation navigates nested data. Cast the resulting value to the intended SQL type when needed.

## FLATTEN
`FLATTEN` converts elements of an array/object into rows, which is useful when a nested array contains repeated child records.

Conceptual pattern:
```sql
SELECT r.id, f.value
FROM raw_events r,
LATERAL FLATTEN(input => r.payload:items) f;
```

## JSON pipeline pattern
```text
JSON files
   ↓
Stage
   ↓
Raw table (VARIANT)
   ↓
Parse/extract
   ↓
Curated relational columns
   ↓
Analytics
```

## Interview pitfalls
- Storing JSON as VARIANT does not remove the need for schema/data-quality thinking.
- Explain why a semi-structured raw layer can be useful, then explain how you expose stable fields to downstream users.
- Do not confuse JSON path extraction with `FLATTEN`; extraction gets values, FLATTEN expands nested collections into rows.
