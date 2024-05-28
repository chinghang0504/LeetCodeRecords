# [LeetCode Records](../../README.md) - Question 1407 Top Travellers

### Attempt 1: Use groupy(), sum(), merge(), fillna(), and sort_values()
```py
import pandas as pd

def top_travellers(users: pd.DataFrame, rides: pd.DataFrame) -> pd.DataFrame:
    total_distance_df = rides.groupby('user_id')['distance'].sum().rename('travelled_distance').reset_index()
    merged_df = pd.merge(users, total_distance_df, left_on='id', right_on='user_id', how='left')[['name', 'travelled_distance']].fillna(0)
    return merged_df.sort_values(['travelled_distance', 'name'], ascending=[False, True])
```
- Runtime: 633 ms (Beats: 91.37%)
- Memory: 67.80 MB (Beats: 33.23%)

<br>
