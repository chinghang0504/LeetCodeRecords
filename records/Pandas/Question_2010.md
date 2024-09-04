# [LeetCode Records](../../README.md) - Question 2010 The Number of Seniors and Juniors to Join the Company II

### Attempt 1: Use cumsum() to get the current budget
```py
import pandas as pd

def number_of_joiners(candidates: pd.DataFrame) -> pd.DataFrame:
    senior_candidates = candidates[candidates['experience'] == 'Senior']
    senior_candidates = senior_candidates.sort_values('salary')
    senior_candidates['cumsum'] = senior_candidates['salary'].cumsum()
    selected_senior_candidates = senior_candidates[senior_candidates['cumsum'] <= 70000]

    junior_candidates = candidates[candidates['experience'] == 'Junior']
    junior_candidates = junior_candidates.sort_values('salary')
    junior_candidates['cumsum'] = junior_candidates['salary'].cumsum()
    senior_budget = selected_senior_candidates['cumsum'].max()
    junior_budget = 70000 if pd.isnull(senior_budget) else 70000 - senior_budget
    
    selected_junior_candidates = junior_candidates[junior_candidates['cumsum'] <= junior_budget]

    return pd.concat([selected_senior_candidates, selected_junior_candidates])[['employee_id']]
```
- Runtime: 364 ms (Beats: 100.00%)
- Memory: 70.35 MB (Beats: 55.00%)

<br>
