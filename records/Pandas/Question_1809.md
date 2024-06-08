# [LeetCode Records](../../README.md) - Question 1809 Ad-Free Sessions

### Attempt 1: Use merge(), isin() and drop_duplicates()
```py
import pandas as pd

def ad_free_sessions(playback: pd.DataFrame, ads: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(playback, ads, on='customer_id')
    session_id_sr = merged_df[(merged_df['start_time'] <= merged_df['timestamp']) & (merged_df['timestamp'] <= merged_df['end_time'])]['session_id']
    return playback[~playback['session_id'].isin(session_id_sr)]['session_id'].drop_duplicates().reset_index()[['session_id']]
```
- Runtime: 500 ms (Beats: 96.43%)
- Memory: 67.70 MB (Beats: 32.14%)

<br>
