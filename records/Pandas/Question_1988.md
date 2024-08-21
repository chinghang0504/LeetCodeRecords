# [LeetCode Records](../../README.md) - Question 1988 Find Cutoff Score for Each School

### Attempt 1: Use pd.merge(), loc(), groupby(), idxmin(), isin(), pd.concat(), and fillna()
```py
import pandas as pd

def find_cutoff_score(schools: pd.DataFrame, exam: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(schools, exam, how='cross')
    merged_df = merged_df[merged_df['capacity'] - merged_df['student_count'] >= 0]
    merged_df = merged_df.loc[merged_df.groupby('school_id')['score'].idxmin()]

    invalid_schools = schools[~schools['school_id'].isin(merged_df['school_id'])]

    return pd.concat([merged_df, invalid_schools])[['school_id', 'score']].fillna(-1)
```
- Runtime: 396 ms (Beats: 93.10%)
- Memory: 83.90 MB (Beats: 17.24%)

<br>
