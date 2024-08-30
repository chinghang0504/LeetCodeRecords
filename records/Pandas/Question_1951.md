# [LeetCode Records](../../README.md) - Question 1951 All the Pairs With the Maximum Number of Common Followers

### Attempt 1: Use groupby(), apply(), pd.merge(), count(), and max()
```py
import pandas as pd

def get_common_relations(df):
    df = pd.merge(df, df, how='cross')
    df = df[df['user_id_x'] < df['user_id_y']]
    return df


def find_pairs(relations: pd.DataFrame) -> pd.DataFrame:
    common_relations = relations.groupby('follower_id').apply(get_common_relations)
    common_counts = common_relations.groupby(['user_id_x', 'user_id_y'])['follower_id_x'].count().rename('count').reset_index()

    ans = common_counts[common_counts['count'] == common_counts['count'].max()]
    return ans.rename(columns={'user_id_x': 'user1_id', 'user_id_y': 'user2_id'})[['user1_id', 'user2_id']]
```
- Runtime: 1355 ms (Beats: 8.70%)
- Memory: 92.15 MB (Beats: 30.43%)

<br>

### Attempt 2: Use pd.merge(), groupby(), count(), and max()
```py
import pandas as pd

def find_pairs(relations: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(relations, relations, on='follower_id')
    merged_df = merged_df[merged_df['user_id_x'] < merged_df['user_id_y']]
    
    common_counts = merged_df.groupby(['user_id_x', 'user_id_y'])['follower_id'].count().rename('count').reset_index()

    ans = common_counts[common_counts['count'] == common_counts['count'].max()]
    return ans.rename(columns={'user_id_x': 'user1_id', 'user_id_y': 'user2_id'})[['user1_id', 'user2_id']]
```
- Runtime: 388 ms (Beats: 91.30%)
- Memory: 88.32 MB (Beats: 78.26%)

<br>
