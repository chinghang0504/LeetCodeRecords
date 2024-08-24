# [LeetCode Records](../../README.md) - Question 2175 The Change in Global Rankings

### Attempt 1: Use pd.merge(), sort_values(), and rank()
```py
import pandas as pd

def global_ratings_change(team_points: pd.DataFrame, points_change: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(team_points, points_change, on='team_id').sort_values('name')

    merged_df['new_points'] = merged_df['points'] + merged_df['points_change']
    merged_df['rank'] = merged_df['points'].rank(method='first', ascending=False)
    merged_df['new_rank'] = merged_df['new_points'].rank(method='first', ascending=False)
    merged_df['rank_diff'] = merged_df['rank'] - merged_df['new_rank']
    return merged_df[['team_id', 'name', 'rank_diff']]
```
- Runtime: 373 ms (Beats: 100.00%)
- Memory: 71.30 MB (Beats: 67.50%)

<br>
