# [LeetCode Records](../../README.md) - Question 3051 Find Candidates for Data Scientist Position 

### Attempt 1: Use isin() and to_frame()
```py
import pandas as pd

def find_candidates(candidates: pd.DataFrame) -> pd.DataFrame:
    python_candidate_id_sr = candidates[candidates['skill'] == 'Python']['candidate_id']
    tableau_candidate_id_sr = candidates[candidates['skill'] == 'Tableau']['candidate_id']
    postgreSQL_candidate_id_sr = candidates[candidates['skill'] == 'PostgreSQL']['candidate_id']
    return python_candidate_id_sr[python_candidate_id_sr.isin(tableau_candidate_id_sr) & python_candidate_id_sr.isin(postgreSQL_candidate_id_sr)].drop_duplicates().to_frame().sort_values('candidate_id')
```
- Runtime: 376 ms (Beats: 96.55%)
- Memory: 66.44 MB (Beats: 58.62%)

<br>
