# [LeetCode Records](../../README.md) - Question 

### Attempt 1: Use sort_values(), groupby(), head(), shift(), np.timedelta64(), np.round(), and nunique()
```py
import pandas as pd

def gameplay_analysis(activity: pd.DataFrame) -> pd.DataFrame:
    sorted_activity = activity.sort_values(['player_id', 'event_date'])

    selected_activity = sorted_activity.groupby('player_id').head(2)
    selected_activity['next_event_date'] = selected_activity.groupby('player_id')['event_date'].shift(-1)
    selected_activity = selected_activity[selected_activity['next_event_date'] - selected_activity['event_date'] == np.timedelta64(1, 'D')]

    return pd.DataFrame({
        'fraction': np.round([selected_activity['player_id'].nunique() / activity['player_id'].nunique()], 2)
    })
```
- Runtime: 367 ms (Beats: 95.72%)
- Memory: 71.62 MB (Beats: 24.39%)

<br>
