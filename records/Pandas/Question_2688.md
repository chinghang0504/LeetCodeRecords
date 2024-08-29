# [LeetCode Records](../../README.md) - Question 2688 Find Active Users

### Attempt 1: Use value_counts(), isin(), sort_values(), shift(), np.timedelta64(), and drop_duplicates()
```py
import pandas as pd

def find_active_users(users: pd.DataFrame) -> pd.DataFrame:
    user_counts = users['user_id'].value_counts().reset_index()
    user_counts = user_counts[user_counts['count'] > 1]

    sorted_users = users[users['user_id'].isin(user_counts['user_id'])].sort_values(['user_id', 'created_at'])
    sorted_users[['next_user_id', 'next_created_at']] = sorted_users[['user_id', 'created_at']].shift(-1)
    sorted_users = sorted_users[sorted_users['user_id'] == sorted_users['next_user_id']]
    sorted_users['diff'] = sorted_users['next_created_at'] - sorted_users['created_at']
    sorted_users['is_within_7_days'] = sorted_users['diff'] <= np.timedelta64(7, 'D')
    return sorted_users[sorted_users['is_within_7_days']][['user_id']].drop_duplicates()
```
- Runtime: 556 ms (Beats: 41.38%)
- Memory: 70.40 MB (Beats: 75.86%)

<br>
