# Pandas / NumPy / Pytest Interview Guide

## Pandas P0
`read_csv`, dtypes, `head`, `info`, `describe`, filtering, `loc`, `iloc`, `sort_values`, `drop_duplicates`, `isna`, `fillna`, `dropna`, `astype`, `groupby`, `agg`, `merge`, `concat`, `apply`, `map`.

## Data-engineering use
Typical flow: ingest → inspect → standardize column names/types → validate required fields → handle nulls → deduplicate → transform → aggregate/join → write output.

## NumPy
Know arrays, vectorized operations, shapes, dtype, indexing, aggregation and why vectorization can outperform Python loops.

## Pytest
Know test function naming, assertions, fixtures, parameterization and isolated unit tests. For data engineering: test schema, null thresholds, duplicates, accepted ranges, row counts and business rules.

## Questions
- `loc` vs `iloc`?
- `merge` vs `concat`?
- `groupby` workflow?
- How do you treat missing numeric values?
- How do you validate an ETL dataset before loading?
- What would you unit-test in a transformation function?
