# [LeetCode Records](../../README.md) - Question 612 Shortest Distance in a Plane

### Attempt 1: Use pd.merge(), apply(), np.round, math.sqrt(), and min()
```py
import pandas as pd

def getDistance(row):
    return (row['x_x'] - row['x_y']) ** 2 + (row['y_x'] - row['y_y']) ** 2


def shortest_distance(point2_d: pd.DataFrame) -> pd.DataFrame:
    points = point2_d.reset_index()

    merged_df = pd.merge(points, points, how='cross')
    merged_df = merged_df[merged_df['index_x'] != merged_df['index_y']]
    merged_df['distance'] = merged_df.apply(getDistance, axis=1)

    return pd.DataFrame({
        'shortest': np.round([math.sqrt(merged_df['distance'].min())], 2)
    })
```
- Runtime: 5935 ms (Beats: 5.82%)
- Memory: 85.27 MB (Beats: 5.82%)

<br>
