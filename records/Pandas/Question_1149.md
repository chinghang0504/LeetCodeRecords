# [LeetCode Records](../../README.md) - Question 1149 Article Views II

### Attempt 1: Use groupby(), nunique(), drop_duplicates(), and sort_values()
```py
import pandas as pd

def article_views(views: pd.DataFrame) -> pd.DataFrame:
    view_count_df = views.groupby(['view_date', 'viewer_id'])['article_id'].nunique().reset_index().rename(columns={'viewer_id': 'id'})
    return view_count_df[view_count_df['article_id'] >= 2][['id']].drop_duplicates().sort_values('id')
```
- Runtime: 542 ms (Beats: 100.00%)
- Memory: 67.54 MB (Beats: 27.27%)

<br>
