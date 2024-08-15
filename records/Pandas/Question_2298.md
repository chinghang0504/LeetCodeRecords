# [LeetCode Records](../../README.md) - Question 2298 Tasks Count in the Weekend

### Attempt 1: Use dt.dayofweek
```py
import pandas as pd

def count_tasks(tasks: pd.DataFrame) -> pd.DataFrame:
    tasks['day_of_week'] = tasks['submit_date'].dt.dayofweek

    total_tasks = len(tasks)
    weekend_tasks = len(tasks[(tasks['day_of_week'] == 5) | (tasks['day_of_week'] == 6)])

    return pd.DataFrame({
        'weekend_cnt': [weekend_tasks],
        'working_cnt': [total_tasks - weekend_tasks]
    })
```
- Runtime: 344 ms (Beats: 92.31%)
- Memory: 69.08 MB (Beats: 65.38%)

<br>
