# [LeetCode Records](../../README.md) - Question 1412 Find the Quiet Students in All Exams

### Attempt 1: Use groupby(), max(), min(), isin(), merge(), and sort_values()
```py
import pandas as pd

def find_quiet_students(student: pd.DataFrame, exam: pd.DataFrame) -> pd.DataFrame:
    max_score_df = exam.groupby('exam_id')['score'].max().reset_index()
    max_score_student_df = pd.merge(exam, max_score_df, on=['exam_id', 'score'])['student_id']
    min_score_df = exam.groupby('exam_id')['score'].min().reset_index()
    min_score_student_df = pd.merge(exam, min_score_df, on=['exam_id', 'score'])['student_id']
    quiet_student_df = exam[~(exam['student_id'].isin(max_score_student_df)) & ~(exam['student_id'].isin(min_score_student_df))]['student_id'].drop_duplicates()
    return pd.merge(student, quiet_student_df, on='student_id').sort_values('student_id')
```
- Runtime: 570 ms (Beats: 90.48%)
- Memory: 66.66 MB (Beats: 52.38%)

<br>
