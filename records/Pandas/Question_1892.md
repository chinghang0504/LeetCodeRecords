# [LeetCode Records](../../README.md) - Question 1892 Page Recommendations II

### Attempt 1: Use pd.merge() to get all pages that at least one friend liked
```py
import pandas as pd

def recommend_page(friendship: pd.DataFrame, likes: pd.DataFrame) -> pd.DataFrame:
    reversed_friendship = friendship.rename(columns={'user1_id': 'user2_id', 'user2_id': 'user1_id'})
    all_friendship = pd.concat([friendship, reversed_friendship])

    merged_df = pd.merge(all_friendship, likes, left_on='user2_id', right_on='user_id')
    merged_df = merged_df.sort_values(['user1_id', 'page_id'])[['user1_id', 'page_id']]

    like_counts = merged_df.groupby(['user1_id', 'page_id']).value_counts().rename('friends_likes').reset_index()
    likes['like'] = True

    ans = pd.merge(like_counts, likes, left_on=['user1_id', 'page_id'], right_on=['user_id', 'page_id'], how='left')
    ans = ans[ans['like'].isna()][['user1_id', 'page_id', 'friends_likes']]
    return ans.rename(columns={'user1_id': 'user_id'})
```
- Runtime: 499 ms (Beats: 100.00%)
- Memory: 79.56 MB (Beats: 91.30%)

<br>
