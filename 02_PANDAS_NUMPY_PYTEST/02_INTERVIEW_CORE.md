# Pandas / NumPy / Matplotlib / Pytest — Interview Core

## Pandas P0
Know `read_csv`, dtypes, `head`, `info`, `describe`, filtering, `loc`, `iloc`, `sort_values`, `drop_duplicates`, `isna`, `fillna`, `dropna`, `astype`, `groupby`, `agg`, `merge`, `concat`, `apply`, `map`.

### Data-engineering flow
Ingest → inspect → standardize columns/types → validate required fields → handle nulls → deduplicate → transform → aggregate/join → validate → write.

### `loc` vs `iloc`
- `loc`: label-based selection.
- `iloc`: integer-position-based selection.

### `merge` vs `concat`
- `merge`: relational-style join using keys.
- `concat`: append/stack objects along an axis.

### Missing data
Choose the treatment from domain semantics. Do not blindly replace missing values with zero or median.

## NumPy
Know arrays, shape, dtype, indexing, vectorized operations and basic aggregation.

```python
import numpy as np
arr = np.array([10, 20, 30])
arr.mean()
```

## Matplotlib
Know basic line, bar and scatter charts, axes labels and when simple visualization helps exploratory analysis.

## Pytest
Know test discovery, assertions, fixtures, parameterization and setup/teardown concepts.

```python
def test_total():
    assert total([1, 2, 3]) == 6
```

### Data-engineering tests
- business-key uniqueness
- null thresholds
- accepted value ranges
- referential integrity
- row-count reconciliation
- schema validation
- freshness checks
- business-rule validation

## Collections
Know `Counter`, `namedtuple` and the historical/use-case role of ordered mappings; prefer modern built-in dict ordering semantics for ordinary mappings where appropriate.

## High-value questions
1. `loc` vs `iloc`?
2. `merge` vs `concat`?
3. How do you handle missing values?
4. How do you detect duplicates?
5. How do you validate a dataset before loading it?
6. What would you unit-test in an ETL transformation?
7. Why vectorization in NumPy/Pandas?
