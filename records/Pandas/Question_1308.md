# [LeetCode Records](../../README.md) - Question 1308 Running Total for Different Genders

### Attempt 1: Use sort_values(), groupby(), and cumsum()
```py
import pandas as pd

def running_total(scores: pd.DataFrame) -> pd.DataFrame:
    sorted_df = scores.sort_values(['gender', 'day'])
    sorted_df['total'] = sorted_df.groupby(['gender'])['score_points'].cumsum()
    return sorted_df[['gender', 'day', 'total']]
```
- Runtime: 580 ms (Beats: 92.11%)
- Memory: 68.10 MB (Beats: 15.79%)

<br>
