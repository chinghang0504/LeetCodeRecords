# [LeetCode Records](../../README.md) - Question 3061 Calculate Trapping Rain Water

### Attempt 1: Get the maximum of left and right height for each height
```py
import pandas as pd

def calculate_trapped_rain_water(heights: pd.DataFrame) -> pd.DataFrame:
    size = len(heights.index)
    height_arr = heights['height']

    left_max_arr = np.zeros(size)
    right_max_arr = np.zeros(size)
    for i in range(1, size - 1):
        left_max_arr[i] = height_arr[0 : i].max()
        right_max_arr[i] = height_arr[i+1 : ].max()

    min_arr = np.minimum(left_max_arr, right_max_arr)
    water_arr = min_arr - height_arr
    water_arr[water_arr < 0] = 0

    return pd.DataFrame({
        'total_trapped_water': [water_arr.sum()]
    })
```
- Runtime: 324 ms (Beats: 100.00%)
- Memory: 68.59 MB (Beats: 100.00%)

<br>
