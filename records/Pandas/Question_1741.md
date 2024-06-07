# [LeetCode Records](../../README.md) - Question 1741 Find Total Time Spent by Each Employee

### Attempt 1: Use groupby() and sum()
```py
import pandas as pd

def total_time(employees: pd.DataFrame) -> pd.DataFrame:
    employees['total_time'] = employees['out_time'] - employees['in_time']
    return employees.groupby(['event_day', 'emp_id'])['total_time'].sum().reset_index().rename(columns={'event_day': 'day'})
```
- Runtime: 504 ms (Beats: 97.97%)
- Memory: 67.06 MB (Beats: 69.47%)

<br>
