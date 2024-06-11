# [LeetCode Records](../../README.md) - Question 1179 Reformat Department Table

### Attempt 1: Use merge()
```py
import pandas as pd

def reformat_table(department: pd.DataFrame) -> pd.DataFrame:
    months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
    dfs = []

    for month in months:
        dfs.append(department[department['month'] == month][['id', 'revenue']].rename(columns={'revenue': f'{month}_Revenue'}))
    
    merged_df = pd.merge(dfs[0], dfs[1], on='id', how='outer')
    for index in range(2, 12):
        merged_df = pd.merge(merged_df, dfs[index], on='id', how='outer')

    return merged_df
```
- Runtime: 845 ms (Beats: 20.28%)
- Memory: 67.26 MB (Beats: 45.16%)

<br>
