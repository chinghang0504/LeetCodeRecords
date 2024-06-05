# [LeetCode Records](../../README.md) - Question 1633 Percentage of Users Attended a Contest

### Attempt 1: Use groupby(), count(), len(), and round()
```py
import pandas as pd

def users_percentage(users: pd.DataFrame, register: pd.DataFrame) -> pd.DataFrame:
    id_count_df = register.groupby('contest_id')['user_id'].count().rename('percentage').reset_index()
    user_count = len(users.index)
    id_count_df['percentage'] = (id_count_df['percentage'] / user_count * 100).round(2)
    return id_count_df.sort_values(['percentage', 'contest_id'], ascending=[False, True])
```
- Runtime: 421 ms (Beats: 100.00%)
- Memory: 69.62 MB (Beats: 55.95%)

<br>
