# [LeetCode Records](../../README.md) - Question 2238 Number of Times a Driver Was a Passenger

### Attempt 1: Use value_counts(), unique(), and pd.merge()
```py
import pandas as pd

def driver_passenger(rides: pd.DataFrame) -> pd.DataFrame:
    counts = rides['passenger_id'].value_counts().rename('cnt').reset_index()

    drivers = pd.DataFrame({
        'driver_id': rides['driver_id'].unique()
    })

    return pd.merge(drivers, counts, left_on='driver_id', right_on='passenger_id', how='left')[['driver_id', 'cnt']].fillna(0)
```
- Runtime: 437 ms (Beats: 67.50%)
- Memory: 70.53 MB (Beats: 67.50%)

<br>
