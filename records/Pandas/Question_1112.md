# [LeetCode Records](../../README.md) - Question 1112 Highest Grade For Each Student

### Attempt 1: Use groupby(), max(), merge(), sort_values(), and drop_duplicates()
```py
import pandas as pd

def highest_grade(enrollments: pd.DataFrame) -> pd.DataFrame:
    max_grade_df = enrollments.groupby('student_id')['grade'].max().reset_index()
    return pd.merge(enrollments, max_grade_df, on=['student_id', 'grade']).sort_values('course_id').drop_duplicates(['student_id']).sort_values('student_id')
```
- Runtime: 578 ms (Beats: 92.19%)
- Memory: 66.34 MB (Beats: 84.38%)

<br>
