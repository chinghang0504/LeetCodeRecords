# [LeetCode Records](../../README.md) - Question 1651 Hopper Company Queries III

### Attempt 1: Calculate the total ride distance and ride duration each month first
```py
import pandas as pd

def hopper_company_queries(drivers: pd.DataFrame, rides: pd.DataFrame, accepted_rides: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(rides, accepted_rides, on='ride_id')
    merged_df = merged_df[merged_df['requested_at'].dt.year == 2020]
    merged_df['month'] = merged_df['requested_at'].dt.month

    totals = merged_df.groupby('month').agg({'ride_distance': 'sum', 'ride_duration': 'sum'}).reset_index()
    months = pd.DataFrame({
        'month': np.arange(1, 13)
    })
    totals = pd.merge(months, totals, on='month', how='outer').fillna(0)
    totals[['second_ride_distance', 'second_ride_duration']] = totals[['ride_distance', 'ride_duration']].shift(-1)
    totals[['third_ride_distance', 'third_ride_duration']] = totals[['ride_distance', 'ride_duration']].shift(-2)
    totals = totals.dropna()
    totals['average_ride_distance'] = np.round((totals['ride_distance'] + totals['second_ride_distance'] + totals['third_ride_distance']) / 3, 2)
    totals['average_ride_duration'] = np.round((totals['ride_duration'] + totals['second_ride_duration'] + totals['third_ride_duration']) / 3, 2)
    return totals[['month', 'average_ride_distance', 'average_ride_duration']]
```
- Runtime: 528 ms (Beats: 95.00%)
- Memory: 72.84 MB (Beats: 40.00%)

<br>
