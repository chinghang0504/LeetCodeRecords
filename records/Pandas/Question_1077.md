# [LeetCode Records](../../README.md) - Question 1077 Project Employees III

### Attempt 1: Use groupby() and max()
```py
import pandas as pd

def project_employees(project: pd.DataFrame, employee: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(project, employee, on='employee_id')
    max_df = merged_df.groupby('project_id')['experience_years'].max().reset_index()
    return pd.merge(merged_df, max_df, on=['project_id', 'experience_years'])[['project_id', 'employee_id']]
```
- Runtime: 544 ms (Beats: 96.00%)
- Memory: 67.19 MB (Beats: 62.67%)

<br>
