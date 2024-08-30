# [LeetCode Records](../../README.md) - Question 614 Second Degree Follower

### Attempt 1: Use value_counts(), is_in(), and sort_values()
```py
import pandas as pd

def second_degree_follower(follow: pd.DataFrame) -> pd.DataFrame:
    follower_counts = follow['followee'].value_counts().rename('num').reset_index()

    ans = follower_counts[follower_counts['followee'].isin(follow['follower'])]
    return ans.rename(columns={'followee': 'follower'}).sort_values('follower')
```
- Runtime: 349 ms (Beats: 92.05%)
- Memory: 69.83 MB (Beats: 85.23%)

<br>
