# Snowflake Time Travel, Fail-safe, Cloning & Retention

## Time Travel
Time Travel provides access to historical data versions within the configured retention period. It supports investigation and recovery scenarios.

## Fail-safe
Fail-safe is a separate, Snowflake-managed recovery period after Time Travel. It is not a general-purpose query mechanism or a substitute for backup strategy.

## Zero-copy cloning
A clone can be created quickly without an immediate full physical copy of the underlying data. Changed data is stored independently as required.

Typical uses:
- development/testing;
- safe experimentation;
- temporary analysis;
- environment creation.

## Time Travel + clone
A clone can be created from a historical point when the relevant object/time-window supports it. This is useful for investigating a prior state without restoring the production object in place.

## Interview comparison
| Feature | Time Travel | Fail-safe | Zero-copy clone |
|---|---|---|---|
| Primary purpose | historical access/recovery | managed recovery | fast independent environment |
| User query tool | yes, within retention | no general interactive mechanism | resulting clone is queryable |
| Storage concept | retained historical data | Snowflake-managed retention | initially shares underlying storage |

## Retention lesson
Do not give a single retention number as universal. Retention depends on object type, edition and account configuration. Always state the governing configuration when answering detailed questions.

## Interview question
**Why use cloning instead of copying a large production table?**
Because a clone can be created quickly without immediately duplicating the full storage footprint, making it practical for testing and analysis. Changes remain isolated from the source.
