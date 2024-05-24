# [LeetCode Records](../../README.md) - Question 1241 Number of Comments per Post

### Attempt 1: Use groupby(), nunique(), and isnull()
```py
import pandas as pd

def count_comments(submissions: pd.DataFrame) -> pd.DataFrame:
    unique_count_df = submissions.groupby('parent_id')['sub_id'].nunique().rename('number_of_comments').reset_index()
    post_df = submissions[submissions['parent_id'].isnull()]['sub_id'].rename('post_id').drop_duplicates().sort_values()
    return pd.merge(post_df, unique_count_df, left_on='post_id', right_on='parent_id', how='left')[['post_id', 'number_of_comments']].fillna(0)
```
- Runtime: 842 ms (Beats: 99.47%)
- Memory: 67.32 MB (Beats: 33.20%)

<br>
