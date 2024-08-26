# [LeetCode Records](../../README.md) - Question 3182 Find Top Scoring Students

### Attempt 1: Use pd.merge(), groupby(), and all()
```py
import pandas as pd

def find_top_scoring_students(enrollments: pd.DataFrame, students: pd.DataFrame, courses: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(students, courses, on='major')
    merged_df = pd.merge(merged_df, enrollments, on=['student_id', 'course_id'], how='left')
    merged_df['is_A'] = merged_df['grade'] == 'A'

    ans = merged_df.groupby('student_id')['is_A'].all().rename('is_all_A').reset_index()
    return ans[ans['is_all_A']][['student_id']]
```
- Runtime: 365 ms (Beats: 100.00%)
- Memory: 71.24 MB (Beats: 50.00%)

<br>
