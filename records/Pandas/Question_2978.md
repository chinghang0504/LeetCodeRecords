# [LeetCode Records](../../README.md) - Question 2978 Symmetric Coordinates

### Attempt 1: Use sort_values(), reset_index(), pd.merge(), and drop_duplicates()
```py
import pandas as pd

def symmetric_pairs(coordinates: pd.DataFrame) -> pd.DataFrame:
    sorted_coordinates = coordinates.sort_values(['X', 'Y'])
    sorted_coordinates = sorted_coordinates.reset_index(drop=True).reset_index()

    merged_df = pd.merge(sorted_coordinates, sorted_coordinates, how='cross')
    merged_df = merged_df[merged_df['index_x'] < merged_df['index_y']]

    ans = merged_df[(merged_df['X_x'] == merged_df['Y_y']) & (merged_df['Y_x'] == merged_df['X_y'])]
    return ans.rename(columns={'X_x': 'x', 'Y_x': 'y'})[['x', 'y']].drop_duplicates()
```
- Runtime: 369 ms (Beats: 87.50%)
- Memory: 71.44 MB (Beats: 6.25%)

<br>
