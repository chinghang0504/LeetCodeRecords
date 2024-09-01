# [LeetCode Records](../../README.md) - Question 1841 League Statistics

### Attempt 1: Use len(), apply(), pd.concat(), groupby(), agg(), sum(), pd.merge(), and sort_values()
```py
import pandas as pd

def get_points(row):
    if row['home_team_goals'] > row['away_team_goals']:
        row['home_team_points'] = 3
        row['away_team_points'] = 0
    elif row['home_team_goals'] < row['away_team_goals']:
        row['home_team_points'] = 0
        row['away_team_points'] = 3
    else:
        row['home_team_points'] = 1
        row['away_team_points'] = 1
    return row


def league_statistics(teams: pd.DataFrame, matches: pd.DataFrame) -> pd.DataFrame:
    if len(matches) == 0:
        return pd.DataFrame({
            'team_name': [],
            'matches_played': [],
            'points': [],
            'goal_for': [],
            'goal_against': [],
            'goal_diff': [],
        })

    points = matches.apply(get_points, axis=1)
    home_team_points = points[['home_team_id', 'home_team_points']].rename(columns={'home_team_id': 'team_id', 'home_team_points': 'points'})
    away_team_points = points[['away_team_id', 'away_team_points']].rename(columns={'away_team_id': 'team_id', 'away_team_points': 'points'})
    points = pd.concat([home_team_points, away_team_points]).groupby('team_id').agg(
        matches_played=('team_id', 'count'),
        points=('points', 'sum')
    ).reset_index()

    home_team_goals = matches[['home_team_id', 'home_team_goals', 'away_team_goals']].rename(columns={'home_team_id': 'team_id', 'home_team_goals': 'goal_for', 'away_team_goals': 'goal_against'})
    away_team_goals = matches[['away_team_id', 'away_team_goals', 'home_team_goals']].rename(columns={'away_team_id': 'team_id', 'away_team_goals': 'goal_for', 'home_team_goals': 'goal_against'})
    goals = pd.concat([home_team_goals, away_team_goals]).groupby('team_id')[['goal_for', 'goal_against']].sum().reset_index()
    goals['goal_diff'] = goals['goal_for'] - goals['goal_against']

    ans = pd.merge(teams, points, on='team_id')
    ans = pd.merge(ans, goals, on='team_id')
    ans = ans.sort_values(['points', 'goal_diff', 'team_name'], ascending=[False, False, True])
    return ans[['team_name', 'matches_played', 'points', 'goal_for', 'goal_against', 'goal_diff']]
```
- Runtime: 2223 ms (Beats: 6.25%)
- Memory: 74.91 MB (Beats: 6.25%)

<br>
