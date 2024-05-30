# [LeetCode Records](../../README.md) - Question 1495 Friendly Movies Streamed Last Month

### Attempt 1: Use dt.year, dt.month, astype(), isin(), and drop_duplicates()
```py
import pandas as pd

def friendly_movies(tv_program: pd.DataFrame, content: pd.DataFrame) -> pd.DataFrame:
    june_content_id_sr = tv_program[(tv_program['program_date'].dt.year == 2020) & (tv_program['program_date'].dt.month == 6)]['content_id']
    return content[(content['Kids_content'] == 'Y') & (content['content_type'] == 'Movies') & (content['content_id'].astype(np.int64).isin(june_content_id_sr))][['title']].drop_duplicates()
```
- Runtime: 631 ms (Beats: 95.74%)
- Memory: 66.99 MB (Beats: 76.60%)

<br>
