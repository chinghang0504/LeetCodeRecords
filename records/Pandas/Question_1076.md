# [LeetCode Records](../../README.md) - Question 1076 Project Employees II

### Attempt 1: Use groupby() and max()
```py
import pandas as pd

def project_employees_ii(project: pd.DataFrame, employee: pd.DataFrame) -> pd.DataFrame:
    count_df = project.groupby('project_id')['employee_id'].count().rename('count').reset_index()
    max_count = count_df['count'].max()
    return count_df[count_df['count'] == max_count][['project_id']]
```
- Runtime: 524 ms (Beats: 96.67%)
- Memory: 66.84 MB (Beats: 36.67%)

<br>
