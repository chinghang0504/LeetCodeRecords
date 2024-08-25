# [LeetCode Records](../../README.md) - Question 3056 Snaps Analysis

### Attempt 1: Use pd.merge(), groupby(), sum(), fillna(), and np.round()
```py
import pandas as pd

def snap_analysis(activities: pd.DataFrame, age: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(activities, age, on='user_id')

    total_activities = merged_df.groupby('age_bucket')['time_spent'].sum().rename('time_total').reset_index()

    open_activities = merged_df[merged_df['activity_type'] == 'open']
    open_activities = open_activities.groupby('age_bucket')['time_spent'].sum().rename('time_open').reset_index()

    send_activities = merged_df[merged_df['activity_type'] == 'send']
    send_activities = send_activities.groupby('age_bucket')['time_spent'].sum().rename('time_send').reset_index()

    ans = pd.merge(total_activities, open_activities, on='age_bucket', how='outer').merge(send_activities, on='age_bucket', how='outer').fillna(0)
    ans['send_perc'] = np.round(ans['time_send'] / ans['time_total'] * 100, 2)
    ans['open_perc'] = np.round(ans['time_open'] / ans['time_total'] * 100, 2)
    return ans[['age_bucket', 'send_perc', 'open_perc']]
```
- Runtime: 413 ms (Beats: 90.70%)
- Memory: 71.52 MB (Beats: 46.51%)

<br>
