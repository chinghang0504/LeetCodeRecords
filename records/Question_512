# [LeetCode Records](../README.md) - Question 512 Game Play Analysis II

### Attempt 1: 
```py
import pandas as pd

def game_analysis(activity: pd.DataFrame) -> pd.DataFrame:
    result_1 = activity.groupby('player_id')['event_date'].min().reset_index()
    result_2 = pd.merge(activity, result_1, on=['player_id', 'event_date'])
    return result_2[['player_id', 'device_id']]
```
- Runtime: 573 ms (Beats: 91.57%)
- Memory: 68.48 MB (Beats: 6.02%)

<br>
