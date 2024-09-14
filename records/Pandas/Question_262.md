# [LeetCode Records](../../README.md) - Question 262 Trips and Users

### Attempt 1: Get all the valid trips first
```py
import pandas as pd

def trips_and_users(trips: pd.DataFrame, users: pd.DataFrame) -> pd.DataFrame:
    trips['request_at'] = pd.to_datetime(trips['request_at'])

    banned_clients = users[(users['role'] == 'client') & (users['banned'] == 'Yes')]
    banned_drivers = users[(users['role'] == 'driver') & (users['banned'] == 'Yes')]

    valid_trips = trips[(trips['request_at'] >= np.datetime64('2013-10-01')) & (trips['request_at'] <= np.datetime64('2013-10-03'))]
    valid_trips = valid_trips[~valid_trips['client_id'].isin(banned_clients['users_id']) & ~valid_trips['driver_id'].isin(banned_drivers['users_id'])]
    valid_trips['is_cancelled'] = valid_trips['status'].apply(lambda status: 0 if status == 'completed' else 1)

    total_counts = valid_trips['request_at'].value_counts().rename('total_count').rename_axis('Day').reset_index()
    cancelled_counts = valid_trips.groupby('request_at')['is_cancelled'].sum().rename('cancelled_count').rename_axis('Day').reset_index()

    ans = pd.merge(total_counts, cancelled_counts, on='Day', how='outer').fillna(0)
    ans['Cancellation Rate'] = np.round(ans['cancelled_count'] / ans['total_count'], 2)
    return ans[['Day', 'Cancellation Rate']]
```
- Runtime: 414 ms (Beats: 68.00%)
- Memory: 72.09 MB (Beats: 5.27%)

<br>
