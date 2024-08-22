# [LeetCode Records](../../README.md) - Question 1264 Page Recommendations

### Attempt 1: Use pd.concat() and isin()
```py
import pandas as pd

def page_recommendations(friendship: pd.DataFrame, likes: pd.DataFrame) -> pd.DataFrame:
    friend_ids = pd.concat([friendship[friendship['user1_id'] == 1]['user2_id'], friendship[friendship['user2_id'] == 1]['user1_id']])

    user1_page_ids = likes[likes['user_id'] == 1]['page_id']

    ans = likes[likes['user_id'].isin(friend_ids)]
    return ans[~ans['page_id'].isin(user1_page_ids)][['page_id']].rename(columns={'page_id': 'recommended_page'}).drop_duplicates()
```
- Runtime: 316 ms (Beats: 100.00%)
- Memory: 69.72 MB (Beats: 40.00%)

<br>
