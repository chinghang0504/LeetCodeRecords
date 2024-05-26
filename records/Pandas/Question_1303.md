# [LeetCode Records](../../README.md) - Question 1303 Find the Team Size

### Attempt 1: Use groupby() and count()
```py
import pandas as pd

def team_size(employee: pd.DataFrame) -> pd.DataFrame:
    team_size_df = employee.groupby('team_id')['employee_id'].count().rename('team_size').reset_index()
    return pd.merge(employee, team_size_df, on='team_id')[['employee_id', 'team_size']]
```
- Runtime: 506 ms (Beats: 96.43%)
- Memory: 66.57 MB (Beats: 51.19%)

<br>
