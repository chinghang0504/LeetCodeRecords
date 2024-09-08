# [LeetCode Records](../../README.md) - Question 1635 Hopper Company Queries I

### Attempt 1: Use cumsum() to get the number of active drivers
```py
import pandas as pd

def hopper_company(drivers: pd.DataFrame, rides: pd.DataFrame, accepted_rides: pd.DataFrame) -> pd.DataFrame:
    drivers['year'] = drivers['join_date'].dt.year
    drivers['month'] = drivers['join_date'].dt.month
    driver_counts = drivers.groupby(['year', 'month'])['driver_id'].count().rename('count').reset_index()
    driver_counts = driver_counts[driver_counts['year'] <= 2020]
    driver_counts['active_drivers'] = driver_counts['count'].cumsum()
    driver_counts = driver_counts[driver_counts['year'] == 2020]
    driver_counts = driver_counts[['month', 'active_drivers']]

    months = pd.DataFrame({
        'month': np.arange(1, 13)
    })
    ans = pd.merge(months, driver_counts, on='month', how='left').fillna(method='ffill')

    rides['year'] = rides['requested_at'].dt.year
    selected_rides = rides[rides['year'] == 2020]
    selected_rides['month'] = selected_rides['requested_at'].dt.month
    merged_df = pd.merge(selected_rides, accepted_rides, on='ride_id')
    merged_df = merged_df.groupby('month')['ride_id'].count().rename('accepted_rides').reset_index()

    return pd.merge(ans, merged_df, on='month', how='outer').fillna(0)
```
- Runtime: 524 ms (Beats: 96.67%)
- Memory: 72.77 MB (Beats: 46.67%)

<br>
