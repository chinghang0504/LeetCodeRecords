# [LeetCode Records](../../README.md) - Question 2995 Viewers Turned Streamers

### Attempt 1: Get the user_id's which the first session is a viewer
```py
import pandas as pd

def count_turned_streamers(sessions: pd.DataFrame) -> pd.DataFrame:
    sorted_sessions = sessions.sort_values(['user_id', 'session_start'])

    first_sessions = sorted_sessions.groupby('user_id').head(1)
    viewer_ids = first_sessions[first_sessions['session_type'] == 'Viewer']['user_id']

    selected_sessions = sessions[sessions['user_id'].isin(viewer_ids)]
    streamer_sessions = selected_sessions[selected_sessions['session_type'] == 'Streamer']

    ans = streamer_sessions['user_id'].value_counts().rename('sessions_count').reset_index()
    return ans.sort_values(['sessions_count', 'user_id'], ascending=[False, False])
```
- Runtime: 341 ms (Beats: 88.89%)
- Memory: 71.22 MB (Beats: 77.78%)

<br>
