# [LeetCode Records](../../README.md) - Question 2041 Accepted Candidates From the Interviews

### Attempt 1: Use groupby(), sum(), and isin()
```py
import pandas as pd

def accepted_candidates(candidates: pd.DataFrame, rounds: pd.DataFrame) -> pd.DataFrame:
    scores = rounds.groupby('interview_id')['score'].sum().reset_index()
    high_scores = scores[scores['score'] > 15]

    high_experience_candidates = candidates[candidates['years_of_exp'] >= 2]

    return high_experience_candidates[high_experience_candidates['interview_id'].isin(high_scores['interview_id'])][['candidate_id']]
```
- Runtime: 417 ms (Beats: 95.06%)
- Memory: 72.07 MB (Beats: 61.60%)

<br>
