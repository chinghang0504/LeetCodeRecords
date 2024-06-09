# [LeetCode Records](../../README.md) - Question 2884 Modify Columns

### Attempt 1: 
```py
import pandas as pd

def modifySalaryColumn(employees: pd.DataFrame) -> pd.DataFrame:
    employees['salary'] = employees['salary'] * 2
    return employees
```
- Runtime: 369 ms (Beats: 98.81%)
- Memory: 65.80 MB (Beats: 5.31%)

<br>
