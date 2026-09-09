# Pandas, NumPy, Matplotlib & Pytest Master Notes

## NumPy
NumPy provides fast array-oriented numerical operations.

```python
import numpy as np
arr = np.array([10, 20, 30])
arr.mean()
arr * 2
```
Know arrays, shape, dtype, indexing, slicing, vectorization and why vectorized operations are usually preferable to Python loops for numerical work.

## Pandas mental model
A `Series` is one labeled column; a `DataFrame` is a tabular collection of labeled columns.

```python
import pandas as pd

df = pd.read_csv("orders.csv")
df = df.drop_duplicates()
df["amount"] = pd.to_numeric(df["amount"], errors="coerce")
df["order_date"] = pd.to_datetime(df["order_date"], errors="coerce")
```

### Essential operations
```python
df.head()
df.info()
df.describe()
df.isna().sum()
df.dropna()
df.fillna(0)
df.groupby("department")["salary"].mean()
df.sort_values("salary", ascending=False)
df.merge(other, on="customer_id", how="left")
df.loc[df["salary"] > 50000, ["name", "salary"]]
df.iloc[:10]
```

### Interview traps
- `loc` uses labels/boolean conditions; `iloc` uses integer positions.
- `merge` is relational joining; `concat` combines along an axis.
- `apply` is flexible but can be slower than vectorized/built-in operations.
- Always inspect dtypes before numeric/date transformations.

## Data cleaning checklist
1. Inspect shape/types.
2. Normalize column names.
3. Convert dates/numerics explicitly.
4. Identify nulls and invalid values.
5. Deduplicate using the correct business key.
6. Apply business rules.
7. Validate ranges and uniqueness.
8. Save a reproducible output.

## Matplotlib
Use it for basic analytical plots: line, bar, scatter, histogram. Know axis labels, title, legend, figure sizing and saving.

## Pytest
Core concepts:
- test discovery
- `assert`
- fixtures
- parametrization
- setup/teardown
- testing pure functions
- data-quality tests

```python
def test_positive_amount():
    assert validate_amount(100) is True
```

### Data-quality tests
Test:
- required columns exist
- primary/business key is unique
- critical columns are non-null
- numeric values are in valid ranges
- dates are valid
- row counts are within expected thresholds

## Collections
`Counter` is ideal for frequency counts; `defaultdict` is useful for grouping; `namedtuple` provides lightweight named fields; `OrderedDict` is mainly relevant when legacy ordering behavior matters.

## Project connection
Project 1 is the main Pandas example: CSV cleaning, date/numeric conversion, null handling, duplicate handling, merging and analytical preparation. Project 2 provides a stronger data-engineering setting for automated validation and pipeline testing.
