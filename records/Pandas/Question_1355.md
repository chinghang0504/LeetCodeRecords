# [LeetCode Records](../../README.md) - Question 1355 Activity Participants

### Attempt 1: Use groupby(), size(), max(), and min()
```py
import pandas as pd

def activity_participants(friends: pd.DataFrame, activities: pd.DataFrame) -> pd.DataFrame:
    activity_counts_sr = friends.groupby('activity').size()
    max_activity_count = activity_counts_sr.max()
    min_activity_count = activity_counts_sr.min()
    return activity_counts_sr[(activity_counts_sr != max_activity_count) & (activity_counts_sr != min_activity_count)].reset_index()[['activity']]
```
- Runtime: 544 ms (Beats: 97.44%)
- Memory: 66.37 MB (Beats: 41.03%)

<br>
