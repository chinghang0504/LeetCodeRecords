# [LeetCode Records](../../README.md) - Question 2004 The Number of Seniors and Juniors to Join the Company

### Attempt 1: Use cumsum() to calculate all the junior salaries from the first to the last
```py
import pandas as pd

def count_seniors_and_juniors(candidates: pd.DataFrame) -> pd.DataFrame:
    senior_candidates = candidates[candidates['experience'] == 'Senior']
    senior_candidates = senior_candidates.sort_values('salary')
    senior_candidates['total_amount'] = senior_candidates['salary'].cumsum()

    total_budget = 70000
    selected_senior_candidates = senior_candidates[senior_candidates['total_amount'] <= total_budget]
    senior_budget = selected_senior_candidates['total_amount'].max()
    junior_budget = total_budget if pd.isna(senior_budget) else total_budget - senior_budget

    junior_candidates = candidates[candidates['experience'] == 'Junior']
    junior_candidates = junior_candidates.sort_values('salary')
    junior_candidates['total_amount'] = junior_candidates['salary'].cumsum()
    selected_junior_candidates = junior_candidates[junior_candidates['total_amount'] <= junior_budget]

    return pd.DataFrame({
        'experience': ['Senior', 'Junior'],
        'accepted_candidates': [len(selected_senior_candidates), len(selected_junior_candidates)]
    })
```
- Runtime: 364 ms (Beats: 100.00%)
- Memory: 69.70 MB (Beats: 83.33%)

<br>
