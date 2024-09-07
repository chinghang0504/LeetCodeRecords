# [LeetCode Records](../../README.md) - Question 1972 First and Last Call On the Same Day

### Attempt 1: Use head(1) to get the first call and tail(1) to get the last call of any day
```py
import pandas as pd

def same_day_calls(calls: pd.DataFrame) -> pd.DataFrame:
    calls['day'] = calls['call_time'].dt.strftime('%Y-%m-%d')
    reversed_calls = calls.rename(columns={'caller_id': 'recipient_id', 'recipient_id': 'caller_id'})

    all_calls = pd.concat([calls, reversed_calls])
    all_calls = all_calls.sort_values(['caller_id', 'call_time'])
    first_calls = all_calls.groupby(['caller_id', 'day']).head(1)
    last_calls = all_calls.groupby(['caller_id', 'day']).tail(1)

    ans = pd.merge(first_calls, last_calls, on=['caller_id', 'recipient_id', 'day'])
    return ans.rename(columns={'caller_id': 'user_id'})[['user_id']].drop_duplicates()
```
- Runtime: 392 ms (Beats: 100.00%)
- Memory: 71.96 MB (Beats: 50.00%)

<br>
