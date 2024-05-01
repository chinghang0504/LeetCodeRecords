# [LeetCode Records](../../README.md) - Question 511 Game Play Analysis I

### Attempt 1: 
```py
import pandas as pd

def game_analysis(activity: pd.DataFrame) -> pd.DataFrame:
    return activity.groupby('player_id')['event_date'].min().reset_index(name='first_login')
```
- Runtime: 535 ms (Beats: 98.17%)
- Memory: 67.86 MB (Beats: 19.23%)

<br>
