# Snowflake Advanced: Cloning, Time Travel, Streams, Tasks

## Zero-copy cloning
A clone is created without immediately making a full independent physical copy of all underlying data. It is useful for development/testing, point-in-time environments and safe experimentation.

## Time Travel
Provides access to historical data within configured retention. Understand query/restore/clone use cases and distinguish it from Fail-safe.

## Streams
Capture change information for supported objects so downstream consumers can process inserts/updates/deletes incrementally.

## Tasks
Schedule or trigger SQL procedures/statements for orchestration. Think DAG-like dependencies for task workflows.

## MERGE
Typical upsert pattern: match on business key; update changed rows; insert new rows. For Type 2, expire the old current version and insert the new version with new effective dates/surrogate key logic.

## QUALIFY
Snowflake-specific filtering of window-function results without forcing an outer query.

## Interview sequence
“Build an incremental pipeline” → stage files → COPY → deduplicate → MERGE → consume changes with Streams → schedule work with Tasks → validate/audit.