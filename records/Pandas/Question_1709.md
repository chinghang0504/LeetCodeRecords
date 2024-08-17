# [LeetCode Records](../../README.md) - Question 1709 Biggest Window Between Visits

### Attempt 1: Use shift(), fillna(), max(), groupby(), and apply()
```py
import pandas as pd

def get_biggest_window(dates):
    return (dates.shift(-1).fillna(np.datetime64('2021-01-01')) - dates).max().days


def biggest_window(user_visits: pd.DataFrame) -> pd.DataFrame:
    sorted_user_visits = user_visits.sort_values(['user_id', 'visit_date'])

    ans = sorted_user_visits.groupby('user_id')['visit_date'].apply(get_biggest_window).rename('biggest_window').reset_index()
    
    return ans.sort_values('user_id')
```
- Runtime: 468 ms (Beats: 73.33%)
- Memory: 70.78 MB (Beats: 46.67%)

<br>
