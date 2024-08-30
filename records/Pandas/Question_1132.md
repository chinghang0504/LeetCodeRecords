# [LeetCode Records](../../README.md) - Question 1132 Reported Posts II

### Attempt 1: Use drop_duplicates(), groupby(), count(), pd.merge(), fillna(), np.round(), and mean()
```py
import pandas as pd

def reported_posts(actions: pd.DataFrame, removals: pd.DataFrame) -> pd.DataFrame:
    reported_posts = actions[(actions['action'] == 'report') & (actions['extra'] == 'spam')][['post_id', 'action_date']].drop_duplicates()
    reported_counts = reported_posts.groupby('action_date')['post_id'].count().rename('reported_count').reset_index()

    removed_posts = pd.merge(reported_posts, removals, on='post_id')
    removed_counts = removed_posts.groupby('action_date')['post_id'].count().rename('removed_count').reset_index()

    merged_df = pd.merge(reported_counts, removed_counts, on='action_date', how='outer').fillna(0)
    merged_df['precentage'] = merged_df['removed_count'] / merged_df['reported_count'] * 100
    return pd.DataFrame({
        'average_daily_percent': np.round([merged_df['precentage'].mean()], 2)
    })
```
- Runtime: 452 ms (Beats: 89.13%)
- Memory: 72.26 MB (Beats: 36.96%)

<br>
