# [LeetCode Records](../../README.md) - Question 1454 Active Users

### Attempt 1: Use sort_values(), drop_duplicates(), shift(), np.timedelta(), and pd.merge()
```py
import pandas as pd

def active_users(accounts: pd.DataFrame, logins: pd.DataFrame) -> pd.DataFrame:
    sorted_logins = logins.sort_values(['id', 'login_date']).drop_duplicates()
    sorted_logins['second_day'] = sorted_logins.groupby('id')['login_date'].shift(-1)
    sorted_logins['third_day'] = sorted_logins.groupby('id')['login_date'].shift(-2)
    sorted_logins['fouth_day'] = sorted_logins.groupby('id')['login_date'].shift(-3)
    sorted_logins['fifth_day'] = sorted_logins.groupby('id')['login_date'].shift(-4)

    one_day = np.timedelta64(1, 'D')
    valid_logins = sorted_logins[
        (sorted_logins['second_day'] - sorted_logins['login_date'] == one_day) &
        (sorted_logins['third_day'] - sorted_logins['second_day'] == one_day) &
        (sorted_logins['fouth_day'] - sorted_logins['third_day'] == one_day) &
        (sorted_logins['fifth_day'] - sorted_logins['fouth_day'] == one_day)
    ]

    return pd.merge(accounts, valid_logins[['id']].drop_duplicates(), on='id').sort_values('id')
```
- Runtime: 537 ms (Beats: 74.60%)
- Memory: 71.59 MB (Beats: 57.14%)

<br>
