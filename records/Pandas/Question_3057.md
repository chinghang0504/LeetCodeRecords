# [LeetCode Records](../../README.md) - Question 3057 Employees Project Allocation

### Attempt 1: Calculate the average workload first
```py
import pandas as pd

def employees_with_above_avg_workload(project: pd.DataFrame, employees: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(project, employees, on='employee_id')
    average_workload = merged_df.groupby('team')['workload'].mean().reset_index()

    ans = pd.merge(merged_df, average_workload, on='team')
    ans = ans[ans['workload_x'] > ans['workload_y']]
    ans = ans.rename(columns={'name': 'employee_name', 'workload_x': 'project_workload'})
    ans = ans.sort_values(['employee_id', 'project_id'])
    return ans[['employee_id', 'project_id', 'employee_name', 'project_workload']]
```
- Runtime: 402 ms (Beats: 94.12%)
- Memory: 71.08 MB (Beats: 88.24%)

<br>
