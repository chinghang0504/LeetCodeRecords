# [LeetCode Records](../../README.md) - Question 1285 Find the Start and End Number of Continuous Ranges

### Attempt 1: Use iloc[], shift(), pd.concat(), and fillna()
```py
import pandas as pd

def find_continuous_ranges(logs: pd.DataFrame) -> pd.DataFrame:
    sorted_logs = logs.sort_values('log_id')
    first_log_id = sorted_logs.iloc[0]['log_id']
    last_log_id = sorted_logs.iloc[-1]['log_id']
    sorted_logs['next_log_id'] = sorted_logs['log_id'].shift(-1)
    sorted_logs = sorted_logs[sorted_logs['log_id'] + 1 != sorted_logs['next_log_id']]

    ans = pd.concat([sorted_logs, pd.DataFrame({'log_id': [last_log_id], 'next_log_id': None})], ignore_index=True)
    ans['start_id'] = ans['next_log_id'].shift(1)
    ans = ans.fillna(first_log_id)
    return ans.rename(columns={'log_id': 'end_id'})[['start_id', 'end_id']]
```
- Runtime: 370 ms (Beats: 92.22%)
- Memory: 69.91 MB (Beats: 60.00%)

<br>
