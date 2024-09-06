# [LeetCode Records](../../README.md) - Question 3278 Find Candidates for Data Scientist Position II

### Attempt 1: Select all the students that have all the skills for that project
```py
import pandas as pd

def get_score(row):
    if row['proficiency'] > row['importance']:
        return 10
    elif row['proficiency'] < row['importance']:
        return -5
    else:
        return 0


def find_best_candidates(candidates: pd.DataFrame, projects: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(projects, candidates, on='skill')
    candidate_skill_counts = merged_df[['project_id', 'candidate_id']].value_counts().reset_index()
    project_skill_counts = projects['project_id'].value_counts().reset_index()
    selected_candidates = pd.merge(candidate_skill_counts, project_skill_counts, on=['project_id', 'count'])

    scores = pd.merge(merged_df, selected_candidates, on=['project_id', 'candidate_id'])
    scores['score'] = scores.apply(get_score, axis=1)
    scores = scores.groupby(['project_id', 'candidate_id'])['score'].sum().reset_index()
    scores = scores.loc[scores.groupby('project_id')['score'].idxmax()]
    scores['score'] = scores['score'] + 100
    return scores
```
- Runtime: 381 ms (Beats: 92.19%)
- Memory: 71.91 MB (Beats: 34.38%)

<br>
