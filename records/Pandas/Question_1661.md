# [LeetCode Records](../../README.md) - Question 1661 Average Time of Process per Machine

### Attempt 1: Use groupby(), mean(), and round()
```py
import pandas as pd

def get_average_time(activity: pd.DataFrame) -> pd.DataFrame:
    sorted_df = activity.sort_values(['machine_id', 'process_id'])
    start_df = sorted_df[sorted_df['activity_type'] == 'start'].reset_index()
    end_df = sorted_df[sorted_df['activity_type'] == 'end'].reset_index()
    end_df['processing_time'] = end_df['timestamp'] - start_df['timestamp']
    return end_df.groupby('machine_id')['processing_time'].mean().round(3).reset_index()
```
- Runtime: 327 ms (Beats: 98.81%)
- Memory: 70.57 MB (Beats: 29.95%)

<br>
