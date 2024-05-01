# [LeetCode Records](../../README.md) - Question 185 Department Top Three Salaries

### Attempt 1: 
```py
import pandas as pd

def top_three_salaries(employee: pd.DataFrame, department: pd.DataFrame) -> pd.DataFrame:
    top_three_salary = employee.drop_duplicates(['salary', 'departmentId']).groupby('departmentId')['salary'].nlargest(3)
    top_three = employee.apply(lambda x: x['salary'] in top_three_salary[x['departmentId']].values, axis=1)
    employee = employee[top_three]
    result = employee.merge(department, left_on='departmentId', right_on='id')
    return pd.DataFrame({
        'Department': result['name_y'],
        'Employee': result['name_x'],
        'Salary': result['salary']
    })
```
- Runtime: 1301 ms (Beats: 5.10%)
- Memory: 67.92 MB (Beats: 27.72%)

<br>
