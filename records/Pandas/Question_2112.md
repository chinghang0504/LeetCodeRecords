# [LeetCode Records](../../README.md) - Question 2112 The Airport With the Most Traffic

### Attempt 1: Use groupby(), sum(), pd.merge(), and max()
```py
import pandas as pd

def airport_with_most_traffic(flights: pd.DataFrame) -> pd.DataFrame:
    departure_counts = flights.groupby('departure_airport')['flights_count'].sum().reset_index().rename(columns={'departure_airport': 'airport_id'})
    arrival_counts = flights.groupby('arrival_airport')['flights_count'].sum().reset_index().rename(columns={'arrival_airport': 'airport_id'})

    ans = pd.merge(departure_counts, arrival_counts, on='airport_id', how='outer').fillna(0)
    ans['total_count'] = ans['flights_count_x'] + ans['flights_count_y']
    max_total_count = ans['total_count'].max()

    return ans[ans['total_count'] == max_total_count][['airport_id']]
```
- Runtime: 398 ms (Beats: 86.05%)
- Memory: 70.93 MB (Beats: 30.23%)

<br>
