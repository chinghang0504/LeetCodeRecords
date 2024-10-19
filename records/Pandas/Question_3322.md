# [LeetCode Records](../../README.md) - Question 3322 Premier League Table Ranking III

### Attempt 1: Use rank() to rank the teams
```py
import pandas as pd

def process_team_standings(season_stats: pd.DataFrame) -> pd.DataFrame:
    season_stats['points'] = season_stats['wins'] * 3 + season_stats['draws']
    season_stats['goal_difference'] = season_stats['goals_for'] - season_stats['goals_against']

    sorted_season_stats = season_stats.sort_values(['season_id', 'points', 'goal_difference', 'team_name'], ascending=[True, False, False, True])
    sorted_season_stats['position'] = sorted_season_stats.groupby('season_id')['points'].rank(method='first', ascending=False)

    return sorted_season_stats[['season_id', 'team_id', 'team_name', 'points', 'goal_difference', 'position']]
```
- Runtime: 376 ms (Beats: 68.42%)
- Memory: 71.07 MB (Beats: 10.53%)

<br>
