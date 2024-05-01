# [LeetCode Records](../../README.md) - Question 184 Department Highest Salary

### Attempt 1: Use groupby(), max(), and merge()
```py
import pandas as pd

def department_highest_salary(employee: pd.DataFrame, department: pd.DataFrame) -> pd.DataFrame:
    max_salary = employee.groupby('departmentId')['salary'].max().reset_index()
    df = employee.merge(max_salary, on=['departmentId', 'salary'])
    df = df.merge(department, left_on='departmentId', right_on='id')
    return pd.DataFrame({'Department': df['name_y'], 'Employee': df['name_x'], 'Salary': df['salary']})
```
- Runtime: 782 ms (Beats: 34.35%)
- Memory: 67.65 MB (Beats: 50.74%)

<br>
