# [LeetCode Records](../../README.md) - Question 1890 The Latest Login in 2020

### Attempt 1: Use groupby and max()
```py
import pandas as pd

def latest_login(logins: pd.DataFrame) -> pd.DataFrame:
    logins_2020 = logins[logins['time_stamp'].dt.year == 2020]
    return logins_2020.groupby('user_id')['time_stamp'].max().rename('last_stamp').reset_index()[['user_id', 'last_stamp']]
```
- Runtime: 446 ms (Beats: 100.00%)
- Memory: 68.43 MB (Beats: 21.52%)

<br>
