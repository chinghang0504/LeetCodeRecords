# [LeetCode Records](../../README.md) - Question 3058 Friends With No Mutual Friends

### Attempt 1: Use pd.concat(), pd.merge(), isna(), and sort_values()
```py
import pandas as pd

def friends_with_no_mutual_friends(friends: pd.DataFrame) -> pd.DataFrame:
    all_friendships = pd.concat([friends, friends.rename(columns={'user_id1': 'user_id2', 'user_id2': 'user_id1'})])

    merged_df = pd.merge(all_friendships, all_friendships, on='user_id2')
    merged_df = merged_df[merged_df['user_id1_x'] != merged_df['user_id1_y']]
    merged_df = merged_df[['user_id1_x', 'user_id1_y']].rename(columns={'user_id1_x': 'user_id1', 'user_id1_y': 'user_id2'})
    merged_df['is_friend'] = True

    ans = pd.merge(friends, merged_df, on=['user_id1', 'user_id2'], how='outer')
    ans = ans[ans['is_friend'].isna()]
    return ans.sort_values(['user_id1', 'user_id2'])[['user_id1', 'user_id2']]
```
- Runtime: 406 ms (Beats: 95.65%)
- Memory: 71.69 MB (Beats: 34.78%)

<br>
