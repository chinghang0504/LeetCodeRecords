# [LeetCode Records](../../README.md) - Question 2720 Popularity Percentage

### Attempt 1: Calculate the number of friends for each user1
```py
import pandas as pd

def popularity_percentage(friends: pd.DataFrame) -> pd.DataFrame:
    reversed_friends = friends.rename(columns={'user1': 'user2', 'user2': 'user1'})
    merged_df = pd.concat([friends, reversed_friends]).drop_duplicates()

    counts = merged_df['user1'].value_counts().reset_index()
    counts['percentage_popularity'] = np.round(counts['count'] / len(counts) * 100, 2)
    return counts.sort_values('user1')[['user1', 'percentage_popularity']]
```
- Runtime: 350 ms (Beats: 84.21%)
- Memory: 70.38 MB (Beats: 47.37%)

<br>
