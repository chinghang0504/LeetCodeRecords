# [LeetCode Records](../../README.md) - Question 1949 Strong Friendship

### Attempt 1: Use pd.concat(), pd.merge(), and value_counts()
```py
import pandas as pd

def strong_friendship(friendship: pd.DataFrame) -> pd.DataFrame:
    all_friendships = pd.concat([friendship, friendship.rename(columns={'user1_id': 'user2_id', 'user2_id': 'user1_id'})])

    merged_df = pd.merge(all_friendships, all_friendships, on='user2_id')
    merged_df = merged_df[(merged_df['user1_id_x'] < merged_df['user1_id_y'])]

    common_friend_counts = merged_df[['user1_id_x', 'user1_id_y']].value_counts().rename('common_friend').reset_index()
    
    ans = common_friend_counts[common_friend_counts['common_friend'] >= 3]
    ans = ans.rename(columns={'user1_id_x': 'user1_id', 'user1_id_y': 'user2_id'})
    
    return pd.merge(ans, all_friendships, on=['user1_id', 'user2_id'])
```
- Runtime: 352 ms (Beats: 100.00%)
- Memory: 76.90 MB (Beats: 59.26%)

<br>
