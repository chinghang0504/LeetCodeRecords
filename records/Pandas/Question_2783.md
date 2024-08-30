# [LeetCode Records](../../README.md) - Question 2783 Flight Occupancy and Waitlist Analysis

### Attempt 1: Use groupby(), count(), pd.merge(), fillna(), min(), and sort_values()
```py
import pandas as pd

def waitlist_analysis(flights: pd.DataFrame, passengers: pd.DataFrame) -> pd.DataFrame:
    passenger_counts = passengers.groupby('flight_id')['passenger_id'].count().rename('count').reset_index()

    ans = pd.merge(flights, passenger_counts, on='flight_id', how='left').fillna(0)
    ans['booked_cnt'] = ans[['capacity', 'count']].min(axis=1)
    ans['waitlist_cnt'] = ans['count'] - ans['booked_cnt']
    return ans.sort_values('flight_id')[['flight_id', 'booked_cnt', 'waitlist_cnt']]
```
- Runtime: 410 ms (Beats: 100.00%)
- Memory: 71.38 MB (Beats: 25.81%)

<br>
