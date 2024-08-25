# [LeetCode Records](../../README.md) - Question 1212 Team Scores in Football Tournament

### Attempt 1: Use apply(), pd.concat(), groupby(), sum(), pd.merge(), fillna(), and sort_values()
```py
import pandas as pd

def getPoints(row):
    if row['host_goals'] > row['guest_goals']:
        row['host_point'] = 3
        row['guest_point'] = 0
    elif row['host_goals'] < row['guest_goals']:
        row['host_point'] = 0
        row['guest_point'] = 3
    else:
        row['host_point'] = 1
        row['guest_point'] = 1
    return row


def team_scores(teams: pd.DataFrame, matches: pd.DataFrame) -> pd.DataFrame:
    matches_with_points = matches.apply(getPoints, axis=1)

    host = matches_with_points[['host_team', 'host_point']].rename(columns={'host_team': 'team_id', 'host_point': 'num_points'})
    guest = matches_with_points[['guest_team', 'guest_point']].rename(columns={'guest_team': 'team_id', 'guest_point': 'num_points'})

    points = pd.concat([host, guest])
    points = points.groupby('team_id')['num_points'].sum().reset_index()

    ans = pd.merge(teams, points, on='team_id', how='outer').fillna(0)
    return ans.sort_values(['num_points', 'team_id'], ascending=[False, True])
```
- Runtime: 779 ms (Beats: 7.69%)
- Memory: 71.91 MB (Beats: 6.41%)

<br>
