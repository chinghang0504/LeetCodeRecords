# [LeetCode Records](../../README.md) - Question 2820 Election Results

### Attempt 1: Use groupby(), count(), pd.merge(), and max()
```py
import pandas as pd

def get_election_results(votes: pd.DataFrame) -> pd.DataFrame:
    voter_counts = votes.groupby('voter')['candidate'].count().rename('count').reset_index()

    merged_df = pd.merge(votes, voter_counts, on='voter')
    merged_df = merged_df[merged_df['count'] > 0]
    merged_df['count'] = 1 / merged_df['count']

    candidates = merged_df.groupby('candidate')['count'].sum().reset_index()
    max_score = candidates['count'].max()

    return candidates[candidates['count'] == max_score][['candidate']].sort_values('candidate')
```
- Runtime: 355 ms (Beats: 97.06%)
- Memory: 70.72 MB (Beats: 55.88%)

<br>
