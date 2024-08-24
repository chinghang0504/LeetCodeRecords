# [LeetCode Records](../../README.md) - Question 574 Winning Candidate

### Attempt 1: Use value_counts(), iloc[], and idxmax()
```py
import pandas as pd

def winning_candidate(candidate: pd.DataFrame, vote: pd.DataFrame) -> pd.DataFrame:
    vote_counts = vote['candidateId'].value_counts().rename('count').reset_index()
    target_id = vote_counts.iloc[vote_counts['count'].idxmax()]['candidateId']
    return candidate[candidate['id'] == target_id][['name']]
```
- Runtime: 351 ms (Beats: 85.19%)
- Memory: 70.22 MB (Beats: 60.74%)

<br>
