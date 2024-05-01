# [LeetCode Records](../../README.md) - Question 175 Combine Two Tables

### Attempt 1: Use pd.merge()
```py
import pandas as pd

def combine_two_tables(person: pd.DataFrame, address: pd.DataFrame) -> pd.DataFrame:
    df = pd.merge(person, address, on='personId', how='left')
    return df[['firstName', 'lastName', 'city', 'state']]
```
- Runtime: 518 ms (Beats: 91.13%)
- Memory: 66.08 MB (Beats: 91.47%)

<br>
