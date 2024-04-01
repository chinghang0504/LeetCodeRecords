# [LeetCode Records](../README.md) - Question 181 Employees Earning More Than Their Managers

### Attempt 1: Join the table first
```py
import pandas as pd

def find_employees(employee: pd.DataFrame) -> pd.DataFrame:
    joined = pd.merge(employee, employee, left_on='managerId', right_on='id')
    result = joined[joined['salary_x'] > joined['salary_y']]['name_x']
    return pd.DataFrame({'Employee': result})
```
- Runtime: 578 ms (Beats: 79.62%)
- Memory: 67.55 MB (Beats: 21.21%)

<br>
