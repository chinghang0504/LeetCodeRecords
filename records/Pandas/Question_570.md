# [LeetCode Records](../../README.md) - Question 570 Managers with at Least 5 Direct Reports

### Attempt 1: Use value_counts() and pd.merge()
```py
import pandas as pd

def find_managers(employee: pd.DataFrame) -> pd.DataFrame:
    counts = employee['managerId'].value_counts().rename('count').reset_index()
    counts = counts[counts['count'] >= 5]

    return pd.merge(employee, counts, left_on='id', right_on='managerId')[['name']]
```
- Runtime: 354 ms (Beats: 87.13%)
- Memory: 72.22 MB (Beats: 7.19%)

<br>
