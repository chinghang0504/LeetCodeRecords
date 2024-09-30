# [LeetCode Records](../../README.md) - Question 3308 Find Top Performing Driver

### Attempt 1: Calculate the ratings and total distances first
```py
import pandas as pd

def get_top_performing_drivers(drivers: pd.DataFrame, vehicles: pd.DataFrame, trips: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(drivers, vehicles, on='driver_id')
    merged_df = pd.merge(merged_df, trips, on='vehicle_id')

    performances = merged_df.groupby(['fuel_type', 'driver_id']).agg({'accidents': 'first', 'distance': 'sum', 'rating': 'mean'}).reset_index()
    performances['rating'] = np.round(performances['rating'], 2)
    performances = performances.sort_values(['fuel_type', 'rating', 'distance', 'accidents'], ascending=[True, False, False, True])
    
    ans = performances.groupby('fuel_type').head(1)
    return ans[['fuel_type', 'driver_id', 'rating', 'distance']]
```
- Runtime: 391 ms (Beats: 100.00%)
- Memory: 72.11 MB (Beats: 100.00%)

<br>
