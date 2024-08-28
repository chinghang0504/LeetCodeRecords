# [LeetCode Records](../../README.md) - Question 2142 The Number of Passengers in Each Bus I

### Attempt 1: Use pd.merge(), loc[], groupby(), idxmin(), count(), fillna(), and sort_values()
```py
import pandas as pd

def count_passengers_in_bus(buses: pd.DataFrame, passengers: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(buses, passengers, how='cross')
    merged_df = merged_df[merged_df['arrival_time_y'] <= merged_df['arrival_time_x']]
    merged_df['diff'] = merged_df['arrival_time_x'] - merged_df['arrival_time_y']
    merged_df = merged_df.loc[merged_df.groupby('passenger_id')['diff'].idxmin()]

    passenger_counts = merged_df.groupby('bus_id')['passenger_id'].count().rename('passengers_cnt').reset_index()
    ans = pd.merge(buses, passenger_counts, on='bus_id', how='left').fillna(0)
    return ans.sort_values('bus_id')[['bus_id', 'passengers_cnt']]
```
- Runtime: 475 ms (Beats: 87.88%)
- Memory: 103.38 MB (Beats: 57.58%)

<br>
