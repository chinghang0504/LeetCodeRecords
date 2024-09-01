# [LeetCode Records](../../README.md) - Question 3089 Find Bursty Behavior

### Attempt 1: Use dt.year, dt.month, dt.day, groupby(), count(), pd.merge(), np.timedelta64(), sum(), and max()
```py
import pandas as pd

def find_bursty_behavior(posts: pd.DataFrame) -> pd.DataFrame:
    selected_posts = posts[(posts['post_date'].dt.year == 2024) & (posts['post_date'].dt.month == 2) & (posts['post_date'].dt.day <= 28)]
    avg_weekly_posts = selected_posts.groupby('user_id')['post_id'].count().rename('avg_weekly_posts').reset_index()
    avg_weekly_posts['avg_weekly_posts'] = avg_weekly_posts['avg_weekly_posts'] / 4

    post_counts = selected_posts.groupby(['user_id', 'post_date'])['post_id'].count().rename('count').reset_index()
    merged_df = pd.merge(post_counts, post_counts, on='user_id')
    merged_df = merged_df[merged_df['post_date_y'] >= merged_df['post_date_x']]
    merged_df['post_date_diff'] = merged_df['post_date_y'] - merged_df['post_date_x']
    merged_df = merged_df[merged_df['post_date_diff'] <= np.timedelta64(6, 'D')]

    max_7day_counts = merged_df.groupby(['user_id', 'post_date_x'])['count_y'].sum().reset_index()
    max_7day_counts = max_7day_counts.groupby('user_id')['count_y'].max().rename('max_7day_posts').reset_index()

    ans = pd.merge(max_7day_counts, avg_weekly_posts, on='user_id')
    return ans[ans['max_7day_posts'] >= ans['avg_weekly_posts'] * 2]
```
- Runtime: 421 ms (Beats: 96.43%)
- Memory: 72.10 MB (Beats: 35.71%)

<br>
