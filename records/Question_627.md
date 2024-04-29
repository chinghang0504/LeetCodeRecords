# [LeetCode Records](../README.md) - Question 627 Swap Salary

### Attempt 1: 
```py
import pandas as pd

def swap_salary(salary: pd.DataFrame) -> pd.DataFrame:
    salary['sex'] = salary['sex'].apply(lambda sex: 'f' if sex == 'm' else 'm')
    return salary
```
- Runtime: 485 ms (Beats: 96.02%)
- Memory: 65.68 MB (Beats: 41.52%)

<br>
