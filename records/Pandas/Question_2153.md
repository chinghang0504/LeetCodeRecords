# [LeetCode Records](../../README.md) - Question 2153 The Number of Passengers in Each Bus II

### Attempt 1: Find the first bus that the passenger can take
```py
import pandas as pd

remaining_pessange_count = 0

def get_pessange_count(row):
    global remaining_pessange_count
    total_count = row['count'] + remaining_pessange_count
    passange_count = min(row['capacity'], total_count)
    remaining_pessange_count = total_count - passange_count
    return passange_count


def number_of_passengers(buses: pd.DataFrame, passengers: pd.DataFrame) -> pd.DataFrame:
    global remaining_pessange_count
    remaining_pessange_count = 0

    merged_df = pd.merge(passengers, buses, how='cross')
    merged_df = merged_df[merged_df['arrival_time_x'] <= merged_df['arrival_time_y']]
    merged_df = merged_df.loc[merged_df.groupby('passenger_id')['arrival_time_y'].idxmin()]

    bus_counts = merged_df['bus_id'].value_counts().rename('count').rename_axis('bus_id').reset_index()

    ans = pd.merge(buses, bus_counts, on='bus_id', how='outer').fillna(0)
    ans = ans.sort_values('arrival_time')

    ans['passengers_cnt'] = ans.apply(get_pessange_count, axis=1)
    return ans.sort_values('bus_id')[['bus_id', 'passengers_cnt']]
```
- Runtime: 513 ms (Beats: 81.82%)
- Memory: 73.68 MB (Beats: 9.09%)

<br>
