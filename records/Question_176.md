# [LeetCode Records](../README.md) - Question 176 Second Highest Salary

### Attempt 1: 
```py
import pandas as pd

def second_highest_salary(employee: pd.DataFrame) -> pd.DataFrame:
    firstMaxSalary = employee['salary'].max()
    employee = employee[employee['salary'] != firstMaxSalary]
    return pd.DataFrame({'SecondHighestSalary': [employee['salary'].max()]})
```
- Runtime: 568 ms (Beats: 56.89%)
- Memory: 65.60 MB (Beats: 71.93%)

<br>
