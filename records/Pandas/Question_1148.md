# [LeetCode Records](../../README.md) - Question 1148 Article Views I

### Attempt 1: 
```py
import pandas as pd

def article_views(views: pd.DataFrame) -> pd.DataFrame:
    result_df = views[views['author_id'] == views['viewer_id']]
    return result_df['author_id'].drop_duplicates().sort_values().rename('id').reset_index()[['id']]
```
- Runtime: 581 ms (Beats: 78.83%)
- Memory: 66.14 MB (Beats: 83.62%)

<br>
