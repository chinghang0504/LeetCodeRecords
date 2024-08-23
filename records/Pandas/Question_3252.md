# [LeetCode Records](../../README.md) - Question 3252 Premier League Table Ranking II

### Attempt 1: Use rank() and apply()
```py
import pandas as pd

def getTier(tier_1_boundary, tier_2_boundary, position):
    if position - 1 <= tier_1_boundary:
        return 'Tier 1'
    elif position - 1 <= tier_2_boundary:
        return 'Tier 2'
    else:
        return 'Tier 3'


def calculate_team_tiers(team_stats: pd.DataFrame) -> pd.DataFrame:
    team_stats['points'] = team_stats['wins'] * 3 + team_stats['draws']

    sorted_team_stats = team_stats.sort_values(['points', 'team_name'], ascending=[False, True])
    sorted_team_stats['position'] = sorted_team_stats['points'].rank(method='min', ascending=False)

    size = len(sorted_team_stats)
    tier_1_boundary = size / 3
    tier_2_boundary = size * 2 / 3
    sorted_team_stats['tier'] = sorted_team_stats['position'].apply(lambda position: getTier(tier_1_boundary, tier_2_boundary, position))

    return sorted_team_stats[['team_name', 'points', 'position', 'tier']]
```
- Runtime: 340 ms (Beats: 94.55%)
- Memory: 70.49 MB (Beats: 61.82%)

<br>
