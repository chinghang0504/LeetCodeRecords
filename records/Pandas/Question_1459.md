# [LeetCode Records](../../README.md) - Question 1459 Rectangles Area

### Attempt 1: Use pd.merge() and abs()
```py
import pandas as pd

def rectangles_area(points: pd.DataFrame) -> pd.DataFrame:
    ans = pd.merge(points, points, how='cross')
    ans['area'] = abs((ans['x_value_x'] - ans['x_value_y']) * (ans['y_value_x'] - ans['y_value_y']))
    ans = ans[(ans['area'] > 0) & (ans['id_x'] < ans['id_y'])].rename(columns={'id_x': 'p1', 'id_y': 'p2'})

    return ans[['p1', 'p2', 'area']].sort_values(['area', 'p1', 'p2'], ascending=[False, True, True])
```
- Runtime: 398 ms (Beats: 92.31%)
- Memory: 71.13 MB (Beats: 23.08%)

<br>
