# [LeetCode Records](../README.md) - Question 178 Rank Scores

### Attempt 1: Get the rank of unique scores first and then join two tables
```py
import pandas as pd

def order_scores(scores: pd.DataFrame) -> pd.DataFrame:
    unique_scores = scores['score'].drop_duplicates()
    unique_scores = unique_scores.sort_values(ascending=False)
    unique_scores = unique_scores.to_frame()
    unique_scores.insert(0, 'rank', range(1, unique_scores.shape[0] + 1))

    scores = scores.merge(unique_scores, on='score')
    scores = scores.sort_values('score', ascending=False)
    return scores[['score', 'rank']]
```
- Runtime: 514 ms (Beats: 88.62%)
- Memory: 67.38 MB (Beats: 29.04%)

<br>
