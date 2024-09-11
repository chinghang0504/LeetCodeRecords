# [LeetCode Records](../../README.md) - Question 3060 User Activities within Time Bounds

### Attempt 1: Consider the overlapping cases
```py
import pandas as pd

def is_overlapping(row):
    start = max(row['session_start_x'], row['session_start_y'])
    end = min(row['session_end_x'], row['session_end_y'])
    return start <= end
    

def user_activities(sessions: pd.DataFrame) -> pd.DataFrame:
    viewer_sessions = sessions[sessions['session_type'] == 'Viewer']
    viewer_sessions = pd.merge(viewer_sessions, viewer_sessions, on='user_id')
    viewer_sessions = viewer_sessions[viewer_sessions['session_id_x'] != viewer_sessions['session_id_y']]

    viewer_sessions['is_overlapping'] = viewer_sessions.apply(is_overlapping, axis=1)
    viewer_overlapping_sessions = viewer_sessions[viewer_sessions['is_overlapping']]

    viewer_sessions = viewer_sessions[viewer_sessions['session_end_x'] <= viewer_sessions['session_start_y']]
    viewer_sessions['time_diff'] = viewer_sessions['session_start_y'] - viewer_sessions['session_end_x']
    viewer_sessions = viewer_sessions[viewer_sessions['time_diff'] <= np.timedelta64(12, 'h')]
    viewer_sessions = pd.concat([viewer_overlapping_sessions, viewer_sessions])

    streamer_sessions = sessions[sessions['session_type'] == 'Streamer']
    streamer_sessions = pd.merge(streamer_sessions, streamer_sessions, on='user_id')
    streamer_sessions = streamer_sessions[streamer_sessions['session_id_x'] != streamer_sessions['session_id_y']]

    streamer_sessions['is_overlapping'] = streamer_sessions.apply(is_overlapping, axis=1)
    streamer_overlapping_sessions = streamer_sessions[streamer_sessions['is_overlapping']]

    streamer_sessions = streamer_sessions[streamer_sessions['session_end_x'] <= streamer_sessions['session_start_y']]
    streamer_sessions['time_diff'] = streamer_sessions['session_start_y'] - streamer_sessions['session_end_x']
    streamer_sessions = streamer_sessions[streamer_sessions['time_diff'] <= np.timedelta64(12, 'h')]
    streamer_sessions = pd.concat([streamer_overlapping_sessions, streamer_sessions])

    ans = pd.concat([viewer_sessions[['user_id']], streamer_sessions[['user_id']]])
    ans = ans.drop_duplicates()
    return ans.sort_values('user_id')
```
- Runtime: 583 ms (Beats: 6.06%)
- Memory: 72.23 MB (Beats: 9.09%)

<br>

### Attempt 2: Use multiple shift() to compare the previous rows
```py
import pandas as pd

def user_activities(sessions: pd.DataFrame) -> pd.DataFrame:
    sorted_sessions = sessions.sort_values(['user_id', 'session_type', 'session_start'])

    ans = sorted_sessions[
        (sorted_sessions['user_id'] == sorted_sessions['user_id'].shift(-1)) &
        (sorted_sessions['session_type'] == sorted_sessions['session_type'].shift(-1)) &
        (sorted_sessions['session_end'] >= sorted_sessions['session_start'].shift(-1) - np.timedelta64(12, 'h'))
    ]
    return ans[['user_id']].drop_duplicates()
```
- Runtime: 396 ms (Beats: 66.67%)
- Memory: 70.74 MB (Beats: 81.82%)

<br>
