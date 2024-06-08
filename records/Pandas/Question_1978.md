# [LeetCode Records](../../README.md) - Question 1978 Employees Whose Manager Left the Company

### Attempt 1: Use isin() and dropna()
```py
import pandas as pd

def find_employees(employees: pd.DataFrame) -> pd.DataFrame:
    selected_employees = employees[~employees['manager_id'].isin(employees['employee_id'])].dropna(subset='manager_id')
    return selected_employees[selected_employees['salary'] < 30000][['employee_id']].sort_values('employee_id')
```
- Runtime: 403 ms (Beats: 98.11%)
- Memory: 67.04 MB (Beats: 6.60%)

<br>
