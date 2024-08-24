# [LeetCode Records](../../README.md) - Question 1747 Leetflex Banned Accounts

### Attempt 1: Use pd.merge(), apply(), eq(), any(), and groupby()
```py
import pandas as pd

def isOverlapping(row):
    if row['ip_address_x'] == row['ip_address_y']:
        return False
    
    max_login = max(row['login_x'], row['logout_y'])
    min_logout = min(row['logout_x'], row['logout_y'])
    return max_login <= min_logout


def checkOverlapping(df):
    merged_df = pd.merge(df, df, how='cross')
    merged_df['is_overlapping'] = merged_df.apply(isOverlapping, axis=1)
    return merged_df['is_overlapping'].eq(True).any()


def leetflex_banned_accnts(log_info: pd.DataFrame) -> pd.DataFrame:
    ans = log_info.groupby('account_id').apply(checkOverlapping).rename('banned').reset_index()
    return ans[ans['banned']][['account_id']]
```
- Runtime: 4950 ms (Beats: 6.12%)
- Memory: 72.13 MB (Beats: 28.57%)

<br>
