# [LeetCode Records](../../README.md) - Question 1729 Find Followers Count

### Attempt 1: Use groupy() and count()
```py
import pandas as pd

def count_followers(followers: pd.DataFrame) -> pd.DataFrame:
    return followers.groupby('user_id')['follower_id'].count().rename('followers_count').reset_index().sort_values('user_id')
```
- Runtime: 448 ms (Beats: 99.21%)
- Memory: 66.51 MB (Beats: 20.05%)

<br>
