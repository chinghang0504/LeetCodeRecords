# [LeetCode Records](../../README.md) - Question 3338 Second Highest Salary II

### Attempt 1: Use rank() to rank the salary
```py
import pandas as pd

def find_second_highest_salary(employees: pd.DataFrame) -> pd.DataFrame:
    employees['rank'] = employees.groupby('dept')['salary'].rank(method='dense', ascending=False)
    selected_employees = employees[employees['rank'] == 2]
    
    ans = selected_employees[['emp_id', 'dept']]
    return ans.sort_values('emp_id')
```
- Runtime: 442 ms (Beats: 100.00%)
- Memory: 70.22 MB (Beats: 100.00%)

<br>
