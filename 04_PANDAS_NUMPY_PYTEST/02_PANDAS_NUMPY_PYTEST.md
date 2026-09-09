# Pandas, NumPy, Matplotlib & Pytest

## NumPy
Array-oriented numerical computing. Know arrays, shape, dtype, indexing, vectorized operations and basic aggregation.

```python
import numpy as np
arr = np.array([10, 20, 30])
arr.mean()
```

## Pandas
DataFrame = labeled two-dimensional tabular structure.

Core interview operations:
```python
df.head()
df.info()
df.describe()
df.drop_duplicates()
df.isna()
df.fillna(...)
df.groupby("department")["salary"].mean()
df.sort_values("salary", ascending=False)
df.merge(other, on="id", how="left")
```

## loc vs iloc
- `loc`: label-based.
- `iloc`: integer-position-based.

## apply / lambda
Use when a vectorized or built-in operation is not suitable. Prefer built-in vectorized operations for clarity/performance when available.

## Missing data
Never choose zero/median blindly. Use domain semantics.

## Matplotlib
Basic plotting for exploratory/analytical visuals. Know line, bar, scatter and labels at a conceptual level.

## Pytest
A Python testing framework.

```python
def test_total():
    assert total([1, 2, 3]) == 6
```

Know:
- test discovery;
- assertions;
- fixtures;
- parameterization;
- setup/teardown concepts.

## Data-engineering tests
Examples:
- uniqueness of business key;
- null threshold;
- accepted values;
- referential integrity;
- row-count reconciliation;
- schema validation;
- freshness.

## Interview scenario
A pipeline produced 5% more records than the source. Explain how you would reconcile counts, identify one-to-many joins, duplicates and retry effects before changing the pipeline.
