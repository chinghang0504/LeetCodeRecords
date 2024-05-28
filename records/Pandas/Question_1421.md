# [LeetCode Records](../../README.md) - Question 1421 NPV Queries

### Attempt 1: Use merge() and fillna()
```py
import pandas as pd

def npv_queries(npv: pd.DataFrame, queries: pd.DataFrame) -> pd.DataFrame:
    return pd.merge(queries, npv, on=['id', 'year'], how='left').fillna(0)
```
- Runtime: 572 ms (Beats: 98.36%)
- Memory: 67.75 MB (Beats: 11.48%)

<br>
