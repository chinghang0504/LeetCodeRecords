# [LeetCode Records](../../README.md) - Question 2020 Number of Accounts That Did Not Stream

### Attempt 1: Use dt.year, isin(), and len()
```py
import pandas as pd

def find_target_accounts(subscriptions: pd.DataFrame, streams: pd.DataFrame) -> pd.DataFrame:
    subscriptions_2021 = subscriptions[(subscriptions['start_date'].dt.year <= 2021) & (2021 <= subscriptions['end_date'].dt.year)]

    streams_2021 = streams[streams['stream_date'].dt.year == 2021]

    return pd.DataFrame({
        'accounts_count': [len(subscriptions_2021[~subscriptions_2021['account_id'].isin(streams_2021['account_id'])])]
    })
```
- Runtime: 356 ms (Beats: 100.00%)
- Memory: 70.46 MB (Beats: 55.00%)

<br>
