# [LeetCode Records](../../README.md) - Question 1142 User Activity for the Past 30 Days II

### Attempt 1: Use groupby(), nunique(), and sum()
```py
import pandas as pd

def user_activity(activity: pd.DataFrame) -> pd.DataFrame:
    end_date = np.datetime64('2019-07-27')
    start_date = end_date - 29
    valid_activity_df = activity[(activity['activity_date'] >= start_date) & (activity['activity_date'] <= end_date)]
    total_users_count = valid_activity_df['user_id'].nunique()
    total_sessions_count = valid_activity_df.groupby('user_id')['session_id'].nunique().sum()
    return pd.DataFrame({
        'average_sessions_per_user': [0 if total_users_count == 0 else round(total_sessions_count / total_users_count, 2)]
    })
```
- Runtime: 546 ms (Beats: 94.55%)
- Memory: 65.55 MB (Beats: 96.36%)

<br>
