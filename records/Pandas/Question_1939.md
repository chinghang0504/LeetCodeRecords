# [LeetCode Records](../../README.md) - Question 1939 Users That Actively Request Confirmation Messages

### Attempt 1: Use groupby() and diff()
```py
import pandas as pd

def find_requesting_users(signups: pd.DataFrame, confirmations: pd.DataFrame) -> pd.DataFrame:
    sorted_confirmations_df = confirmations.sort_values(['user_id', 'time_stamp'])
    sorted_confirmations_df['diff'] = sorted_confirmations_df.groupby('user_id')['time_stamp'].diff()
    return sorted_confirmations_df[sorted_confirmations_df['diff'] <= np.timedelta64(1, 'D')].drop_duplicates('user_id')[['user_id']]
```
- Runtime: 419 ms (Beats: 100.00%)
- Memory: 67.47 MB (Beats: 69.57%)

<br>
