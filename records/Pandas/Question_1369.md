# [LeetCode Records](../../README.md) - Question 1369 Get the Second Most Recent Activity

### Attempt 1: Use tail(2) to find the most two recent activities and head(1) to find the second most recent activities
```py
import pandas as pd

def second_most_recent(user_activity: pd.DataFrame) -> pd.DataFrame:
    most_two_recent_activities = user_activity.groupby(['username', 'activity'])['endDate'].max().reset_index()
    most_two_recent_activities = most_two_recent_activities.sort_values(['username', 'endDate'])
    most_two_recent_activities = most_two_recent_activities.groupby('username').tail(2)
    
    second_most_recent_activities = most_two_recent_activities.groupby('username').head(1)

    return pd.merge(second_most_recent_activities, user_activity, on=['username', 'activity', 'endDate'])
```
- Runtime: 383 ms (Beats: 94.12%)
- Memory: 71.40 MB (Beats: 19.61%)

<br>
