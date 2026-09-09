# NumPy / Pandas / Pytest Master Notes

## Curriculum
NumPy, Matplotlib, Pytest, Pandas and Collections module.

## NumPy
Array-oriented numerical computing. Know arrays, shape, dtype, indexing/slicing, vectorized operations, aggregation and broadcasting at a practical level.

## Pandas mental model
`Series` = one-dimensional labeled data. `DataFrame` = tabular labeled data.

### P0 operations
```python
read_csv()
head()
info()
dtypes
isna()
fillna()
dropna()
drop_duplicates()
sort_values()
groupby()
agg()
merge()
join()
loc
iloc
apply()
```

### Data-engineering example
```python
df = pd.read_csv("orders.csv")
df = df.drop_duplicates()
df["order_date"] = pd.to_datetime(df["order_date"], errors="coerce")
df["amount"] = pd.to_numeric(df["amount"], errors="coerce")
df["amount"] = df["amount"].fillna(0)
summary = df.groupby("customer_id", as_index=False)["amount"].sum()
```

## Pytest
Know tests, assertions, fixtures and parameterization. For data pipelines, test schema, null constraints, duplicates, accepted ranges and key relationships.

## Collections
`Counter` for frequencies; `namedtuple` for lightweight named records; `OrderedDict` history is relevant but modern Python dicts preserve insertion order, so explain the compatibility/use-case distinction rather than memorizing old claims.

## Interview questions
- Pandas vs NumPy.
- `loc` vs `iloc`.
- `merge` vs `concat`.
- How do you handle missing values?
- How do you remove duplicates?
- How do you group/aggregate?
- How would you test a data-cleaning pipeline?

## Project connection
Disaster project: Pandas is the actual ETL layer, including date/numeric conversion, missing-value handling, deduplication and aggregation.
