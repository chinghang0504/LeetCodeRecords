# [LeetCode Records](../../README.md) - Question 534 

### Attempt 1: Use groupby() and cumsum()
```py
import pandas as pd

def gameplay_analysis(activity: pd.DataFrame) -> pd.DataFrame:
    sorted_df = activity.sort_values('event_date')
    sorted_df['games_played_so_far'] = sorted_df.groupby('player_id')['games_played'].cumsum()
    return sorted_df[['player_id', 'event_date', 'games_played_so_far']]
```
- Runtime: 571 ms (Beats: 99.12%)
- Memory: 68.17 MB (Beats: 58.77%)

<br>
