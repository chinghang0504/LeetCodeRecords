# [LeetCode Records](../../README.md) - Question 1789 Primary Department for Each Employee 

### Attempt 1: Use groupby(), count(), isin(), and pd.concat()
```py
import pandas as pd

def find_primary_department(employee: pd.DataFrame) -> pd.DataFrame:
    multidepartment_employee_df = employee[employee['primary_flag'] == 'Y']
    employee_count = employee.groupby('employee_id')['employee_id'].count()
    one_department_employee_df = employee[employee['employee_id'].isin(employee_count[employee_count == 1].index)]
    return pd.concat([one_department_employee_df, multidepartment_employee_df])[['employee_id', 'department_id']].drop_duplicates()
```
- Runtime: 367 ms (Beats: 96.68%)
- Memory: 70.62 MB (Beats: 13.51%)

<br>
