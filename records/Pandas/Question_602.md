# [LeetCode Records](../../README.md) - Question 602 Friend Requests II: Who Has the Most Friends

### Attempt 1: Use value_counts(), pd.merge(), fillna(), and max()
```py
import pandas as pd

def most_friends(request_accepted: pd.DataFrame) -> pd.DataFrame:
    requester_counts = request_accepted['requester_id'].value_counts().reset_index().rename(columns={'requester_id': 'id', 'count': 'requester_count'})
    accepter_counts = request_accepted['accepter_id'].value_counts().reset_index().rename(columns={'accepter_id': 'id', 'count': 'accepter_count'})

    merged_df = pd.merge(requester_counts, accepter_counts, on='id', how='outer').fillna(0)
    merged_df['num'] = merged_df['requester_count'] + merged_df['accepter_count']
    
    most_friend = merged_df[merged_df['num'] == merged_df['num'].max()]
    return most_friend[['id', 'num']]
```
- Runtime: 352 ms (Beats: 84.47%)
- Memory: 71.03 MB (Beats: 6.50%)

<br>
