# [LeetCode Records](../../README.md) - Question 1107 New Users Daily Count

### Attempt 1: Use groupby(), min(), np.datetime64(), and value_counts()
```py
import pandas as pd

def new_users_daily_count(traffic: pd.DataFrame) -> pd.DataFrame:
    login_traffic = traffic[traffic['activity'] == 'login']

    first_time_login_traffic = login_traffic.groupby('user_id')['activity_date'].min().reset_index()
    start_date = np.datetime64('2019-06-30') - 90
    first_time_login_traffic = first_time_login_traffic[first_time_login_traffic['activity_date'] >= start_date]
    first_time_login_traffic = first_time_login_traffic['activity_date'].value_counts()
    return first_time_login_traffic.reset_index().rename(columns={'activity_date': 'login_date', 'count': 'user_count'})
```
- Runtime: 382 ms (Beats: 94.12%)
- Memory: 71.28 MB (Beats: 75.00%)

<br>
