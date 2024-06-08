# [LeetCode Records](../../README.md) - Question 1965 Employees With Missing Information

### Attempt 1: Use isin() and concat()
```py
import pandas as pd

def find_employees(employees: pd.DataFrame, salaries: pd.DataFrame) -> pd.DataFrame:
    missing_in_employees_df = employees[~employees['employee_id'].isin(salaries['employee_id'])]
    missing_in_salaries_df = salaries[~salaries['employee_id'].isin(employees['employee_id'])]
    return pd.concat([missing_in_employees_df, missing_in_salaries_df])[['employee_id']].sort_values('employee_id')
```
- Runtime: 393 ms (Beats: 96.15%)
- Memory: 66.95 MB (Beats: 23.93%)

<br>
