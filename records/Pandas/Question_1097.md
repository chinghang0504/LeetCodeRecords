# [LeetCode Records](../../README.md) - Question 1097 Game Play Analysis V

### Attempt 1: Use head(2) to get the two first activities of each player
```py
import pandas as pd
from decimal import Decimal, ROUND_HALF_UP

def get_retention(row):
    if row['next_event_date'] == None:
        return 0
    elif row['next_event_date'] - row['event_date'] != np.timedelta64(1, 'D'):
        return 0
    elif row['next_games_played'] == 0:
        return 0
    
    return 1


def gameplay_analysis(activity: pd.DataFrame) -> pd.DataFrame:
    sorted_activity = activity.sort_values(['player_id', 'event_date'])

    selected_activity = sorted_activity.groupby('player_id').head(2)
    selected_activity[['next_event_date', 'next_games_played']] = selected_activity.groupby('player_id')[['event_date', 'games_played']].shift(-1)
    selected_activity = selected_activity.groupby('player_id').head(1)
    selected_activity['retention'] = selected_activity.apply(get_retention, axis=1)
    
    ans = selected_activity.groupby('event_date').agg(
        installs=('player_id', 'count'),
        Day1_retention=('retention', 'sum')
    ).reset_index()
    ans['Day1_retention'] = ans['Day1_retention'] / ans['installs']
    ans['Day1_retention'] = ans['Day1_retention'].apply(lambda x: Decimal(str(x)).quantize(Decimal('0.01'), rounding=ROUND_HALF_UP))
    return ans.rename(columns={'event_date': 'install_dt'})
```
- Runtime: 458 ms (Beats: 81.08%)
- Memory: 72.23 MB (Beats: 43.24%)

<br>
