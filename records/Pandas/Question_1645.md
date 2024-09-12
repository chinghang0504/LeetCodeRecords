# [LeetCode Records](../../README.md) - Question 1645 Hopper Company Queries II

### Attempt 1: Calculate the accepted ride counts and the driver counts
```py
import pandas as pd

def hopper_company_queries(drivers: pd.DataFrame, rides: pd.DataFrame, accepted_rides: pd.DataFrame) -> pd.DataFrame:
    rides_2020 = rides[rides['requested_at'].dt.year == 2020]
    rides_2020['month'] = rides_2020['requested_at'].dt.month
    accepted_rides_2020 = pd.merge(rides_2020, accepted_rides, on='ride_id')
    accepted_ride_counts = accepted_rides_2020.groupby('month')['driver_id'].nunique().rename('ride_count').reset_index()

    drivers['year'] = drivers['join_date'].dt.year
    drivers['month'] = drivers['join_date'].dt.month
    driver_counts = drivers.groupby(['year', 'month'])['driver_id'].nunique().rename('driver_count').reset_index()
    driver_counts['driver_cumsum'] = driver_counts['driver_count'].cumsum()
    driver_counts = driver_counts[driver_counts['year'] == 2020]
    driver_counts = driver_counts[['month', 'driver_cumsum']]

    months = pd.DataFrame({
        'month': np.arange(1, 13)
    })
    ans = pd.merge(months, driver_counts, on='month', how='outer').fillna(method='ffill')
    ans = pd.merge(ans, accepted_ride_counts, on='month', how='outer').fillna(0)
    ans['working_percentage'] = np.nan_to_num(np.round(ans['ride_count'] / ans['driver_cumsum'] * 100, 2))
    return ans[['month', 'working_percentage']]
```
- Runtime: 548 ms (Beats: 95.00%)
- Memory: 72.83 MB (Beats: 50.00%)

<br>
