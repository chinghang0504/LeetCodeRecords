# [LeetCode Records](../../README.md) - Question 1783 Grand Slam Titles

### Attempt 1: Use concat(), value_counts(), and merge()
```py
import pandas as pd

def grand_slam_titles(players: pd.DataFrame, championships: pd.DataFrame) -> pd.DataFrame:
    count_df = pd.concat([championships['Wimbledon'], championships['Fr_open'], championships['US_open'], championships['Au_open']]).value_counts().reset_index().rename(columns={'index': 'player_id', 'count': 'grand_slams_count'})
    return pd.merge(players, count_df, on='player_id')
```
- Runtime: 502 ms (Beats: 100.00%)
- Memory: 67.40 MB (Beats: 17.50%)

<br>
