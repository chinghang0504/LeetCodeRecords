# [LeetCode Records](../../README.md) - Question 1731 The Number of Employees Which Report to Each Employee

### Attempt 1: Use isna(), groupby(), agg(), apply(), and pd.merge()
```py
import pandas as pd

def count_employees(employees: pd.DataFrame) -> pd.DataFrame:
    count_mean_df = employees[~employees['reports_to'].isna()].groupby('reports_to').agg({'employee_id': 'count', 'age': 'mean'}).reset_index()
    count_mean_df['age'] = count_mean_df['age'].apply(lambda x: int(x + 0.5))
    count_mean_df = count_mean_df.rename(columns={'reports_to': 'employee_id', 'employee_id': 'reports_count', 'age': 'average_age'})
    return pd.merge(count_mean_df, employees, on='employee_id')[['employee_id','name','reports_count','average_age']].sort_values('employee_id')

```
- Runtime: 454 ms (Beats: 95.36%)
- Memory: 71.94 MB (Beats: 10.43%)

<br>
