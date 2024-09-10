# [LeetCode Records](../../README.md) - Question 1919 Leetcodify Similar Friends

### Attempt 1: Use pd.merge() twice to get the same song_id and day of a friendship
```py
import pandas as pd

def leetcodify_similar_friends(listens: pd.DataFrame, friendship: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(friendship, listens.rename(columns={'user_id': 'user1_id'}), on='user1_id')
    merged_df = pd.merge(merged_df, listens.rename(columns={'user_id': 'user2_id'}), on=['user2_id', 'song_id', 'day'])

    counts = merged_df.groupby(['user1_id', 'user2_id', 'day'])['song_id'].nunique().rename('count').reset_index()
    return counts[counts['count'] >= 3][['user1_id', 'user2_id']].drop_duplicates()
```
- Runtime: 588 ms (Beats: 56.00%)
- Memory: 183.25 MB (Beats: 8.00%)

<br>
