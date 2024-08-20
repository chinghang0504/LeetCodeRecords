# [LeetCode Records](../../README.md) - Question 1875 Group Employees of the Same Salary

### Attempt 1: Use groupby(), count(), rank(), and pd.merge()
```py
import pandas as pd

def employees_of_same_salary(employees: pd.DataFrame) -> pd.DataFrame:
    salary_groups = employees.groupby('salary')['employee_id'].count().rename('count').reset_index()
    salary_groups = salary_groups[salary_groups['count'] >= 2]
    salary_groups['team_id'] = salary_groups['salary'].rank(method='min')

    return pd.merge(employees, salary_groups, on='salary').sort_values(['team_id', 'employee_id'])[['employee_id', 'name', 'salary', 'team_id']]
```
- Runtime: 409 ms (Beats: 81.25%)
- Memory: 71.80 MB (Beats: 18.75%)

<br>
