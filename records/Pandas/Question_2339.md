# [LeetCode Records](../../README.md) - Question 2339 All the Matches of the League

### Attempt 1: Use merge()
```py
import pandas as pd

def find_all_matches(teams: pd.DataFrame) -> pd.DataFrame:
    cross_product_df = pd.merge(teams, teams, how='cross').rename(columns={'team_name_x': 'home_team', 'team_name_y': 'away_team'})
    return cross_product_df[cross_product_df['home_team'] != cross_product_df['away_team']]
```
- Runtime: 408 ms (Beats: 96.15%)
- Memory: 67.28 MB (Beats: 34.62%)

<br>
