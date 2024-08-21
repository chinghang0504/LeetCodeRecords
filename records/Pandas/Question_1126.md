# [LeetCode Records](../../README.md) - Question 1126 Active Businesses

### Attempt 1: Use groupby(), mean(), pd.merge(), and count()
```py
import pandas as pd

def active_businesses(events: pd.DataFrame) -> pd.DataFrame:
    event_averages = events.groupby('event_type')['occurrences'].mean().rename('average').reset_index()

    merged_df = pd.merge(events, event_averages, on='event_type')
    merged_df = merged_df[merged_df['occurrences'] > merged_df['average']]

    event_counts = merged_df.groupby('business_id')['event_type'].count().rename('count').reset_index()
    
    return event_counts[event_counts['count'] > 1][['business_id']]
```
- Runtime: 404 ms (Beats: 88.51%)
- Memory: 72.28 MB (Beats: 29.88%)

<br>
