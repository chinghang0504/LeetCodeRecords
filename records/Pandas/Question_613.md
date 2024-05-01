# [LeetCode Records](../../README.md) - Question 613 Shortest Distance in a Line

### Attempt 1: 
```py
import pandas as pd

def shortest_distance(point: pd.DataFrame) -> pd.DataFrame:
    point.sort_values('x', inplace=True)
    point['next_x'] = point['x'].shift(-1)
    point['distance'] = point['next_x'] - point['x']
    return pd.DataFrame({
        'shortest': [point['distance'].min()]
    })
```
- Runtime: 511 ms (Beats: 93.88%)
- Memory: 65.90 MB (Beats: 57.14%)

<br>
