# [LeetCode Records](../../README.md) - Question 1378 Replace Employee ID With The Unique Identifier

### Attempt 1: Use merge()
```py
import pandas as pd

def replace_employee_id(employees: pd.DataFrame, employee_uni: pd.DataFrame) -> pd.DataFrame:
    return pd.merge(employees, employee_uni, on='id', how='left')[['unique_id', 'name']]
```
- Runtime: 578 ms (Beats: 96.44%)
- Memory: 66.60 MB (Beats: 74.30%)

<br>
