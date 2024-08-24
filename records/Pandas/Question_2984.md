# [LeetCode Records](../../README.md) - Question 2984 Find Peak Calling Hours for Each City

### Attempt 1: Use dt.hour, groupby(), value_counts(), max(), and pd.merge()
```py
import pandas as pd

def peak_calling_hours(calls: pd.DataFrame) -> pd.DataFrame:
    calls['peak_calling_hour'] = calls['call_time'].dt.hour

    counts = calls.groupby('city')['peak_calling_hour'].value_counts().rename('number_of_calls').reset_index()
    max_counts = counts.groupby('city')['number_of_calls'].max().reset_index()

    ans = pd.merge(counts, max_counts, on=['city', 'number_of_calls'])
    return ans.sort_values(['peak_calling_hour', 'city'], ascending=[False, False])
```
- Runtime: 392 ms (Beats: 98.00%)
- Memory: 72.24 MB (Beats: 18.00%)

<br>
