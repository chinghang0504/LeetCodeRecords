# [LeetCode Records](../../README.md) - Question 1075 Project Employees I

### Attempt 1: Use groupby() and mean()
```py
import pandas as pd

def project_employees_i(project: pd.DataFrame, employee: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(project, employee, on='employee_id')
    return merged_df.groupby('project_id')['experience_years'].mean().rename('average_years').round(2).reset_index()
```
- Runtime: 510 ms (Beats: 99.46%)
- Memory: 67.30 MB (Beats: 71.56%)

<br>
