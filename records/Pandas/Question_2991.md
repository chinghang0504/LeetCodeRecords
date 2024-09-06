# [LeetCode Records](../../README.md) - Question 2991 Top Three Wineries

### Attempt 1: Use rank() to get the top 3 wineries
```py
import pandas as pd

def top_three_wineries(wineries: pd.DataFrame) -> pd.DataFrame:
    total_points = wineries.groupby(['country', 'winery'])['points'].sum().reset_index()

    sorted_wineries = total_points.sort_values(['country', 'points', 'winery'], ascending=[True, False, True])
    sorted_wineries = sorted_wineries.groupby('country').head(3)
    sorted_wineries['rank'] = sorted_wineries.groupby('country')['points'].rank(method='first', ascending=False)
    sorted_wineries['winery'] = sorted_wineries.apply(lambda row: f'{row["winery"]} ({row["points"]})', axis=1)

    top_winery = sorted_wineries[sorted_wineries['rank'] == 1][['country', 'winery']].rename(columns={'winery': 'top_winery'})
    second_winery = sorted_wineries[sorted_wineries['rank'] == 2][['country', 'winery']].rename(columns={'winery': 'second_winery'})
    third_winery = sorted_wineries[sorted_wineries['rank'] == 3][['country', 'winery']].rename(columns={'winery': 'third_winery'})

    ans = pd.merge(top_winery, second_winery, on='country', how='outer')
    ans = pd.merge(ans, third_winery, on='country', how='outer')
    ans['second_winery'] = ans['second_winery'].fillna('No second winery')
    ans['third_winery'] = ans['third_winery'].fillna('No third winery')
    return ans.sort_values('country')
```
- Runtime: 403 ms (Beats: 100.00%)
- Memory: 72.18 MB (Beats: 20.00%)

<br>
