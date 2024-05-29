# [LeetCode Records](../../README.md) - Question 1141 User Activity for the Past 30 Days I

### Attempt 1: Use groupby() and nunique()
```py
import pandas as pd

def user_activity(activity: pd.DataFrame) -> pd.DataFrame:
    end_date = np.datetime64('2019-07-27')
    start_date = end_date - 29
    valid_activity_df = activity[(activity['activity_date'] >= start_date) & (activity['activity_date'] <= end_date)]
    return valid_activity_df.groupby('activity_date')['user_id'].nunique().reset_index().rename(columns={'activity_date': 'day', 'user_id': 'active_users'})
```
- Runtime: 568 ms (Beats: 95.26%)
- Memory: 67.10 MB (Beats: 83.18%)

<br>
