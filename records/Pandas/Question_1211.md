# [LeetCode Records](../../README.md) - Question 1211 Queries Quality and Percentage

### Attempt 1: Use groupby(), mean(), apply(), value_counts(), and pd.merge()
```py
import pandas as pd

def queries_stats(queries: pd.DataFrame) -> pd.DataFrame:
    queries['quality'] = queries['rating'] / queries['position']
    quality_df = queries.groupby('query_name')['quality'].mean().reset_index()
    quality_df['quality'] = quality_df['quality'].apply(lambda x: int(x * 100 + 0.5) / 100)
    poor_df = (queries[queries['rating'] < 3]['query_name'].value_counts() / queries['query_name'].value_counts() * 100).fillna(0).reset_index().rename(columns={'poor_query_percentage': 'query_name', 'count': 'poor_query_percentage'})
    poor_df['poor_query_percentage'] = poor_df['poor_query_percentage'].apply(lambda x: int(x * 100 + 0.5) / 100)
    return pd.merge(quality_df, poor_df, on='query_name')
```
- Runtime: 367 ms (Beats: 88.37%)
- Memory: 71.46 MB (Beats: 6.49%)

<br>
