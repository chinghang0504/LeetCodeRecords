# [LeetCode Records](../../README.md) - Question 2988 Manager of the Largest Department

### Attempt 1: Use groupby(), count(), max(), and pd.merge()
```py
import pandas as pd

def find_manager(employees: pd.DataFrame) -> pd.DataFrame:
    employee_counts = employees.groupby('dep_id')['emp_id'].count()
    max_employee_count = employee_counts.max()
    max_employee_department_ids = employee_counts[employee_counts == max_employee_count].reset_index()

    managers = employees[employees['position'] == 'Manager']

    ans = pd.merge(max_employee_department_ids, managers, on='dep_id').rename(columns={'emp_name':'manager_name'})
    return ans[['manager_name','dep_id']].sort_values('dep_id')
```
- Runtime: 353 ms (Beats: 90.00%)
- Memory: 70.66 MB (Beats: 40.00%)

<br>
