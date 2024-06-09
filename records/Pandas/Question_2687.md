# [LeetCode Records](../../README.md) - Question 2687 Bikes Last Time Used

### Attempt 1: Use groupby() and max()
```py
import pandas as pd

def last_used_time(bikes: pd.DataFrame) -> pd.DataFrame:
    return bikes.groupby('bike_number')['end_time'].max().reset_index()[['bike_number', 'end_time']].sort_values('end_time', ascending=False)
```
- Runtime: 390 ms (Beats: 100.00%)
- Memory: 67.54 MB (Beats: 26.32%)

<br>
