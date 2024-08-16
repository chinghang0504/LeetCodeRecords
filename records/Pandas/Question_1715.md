# [LeetCode Records](../../README.md) - Question 1715 Count Apples and Oranges

### Attempt 1: Use pd.merge() and sum()
```py
import pandas as pd

def count_apples_and_oranges(boxes: pd.DataFrame, chests: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(boxes, chests, on='chest_id', how='left')

    apple_count = merged_df['apple_count_x'].sum() + merged_df['apple_count_y'].sum()
    orange_count = merged_df['orange_count_x'].sum() + merged_df['orange_count_y'].sum()

    return pd.DataFrame({
        'apple_count': [apple_count],
        'orange_count': [orange_count]
    })
```
- Runtime: 382 ms (Beats: 100.00%)
- Memory: 71.23 MB (Beats: 15.38%)

<br>
