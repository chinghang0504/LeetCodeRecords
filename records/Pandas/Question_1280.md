# [LeetCode Records](../../README.md) - Question 1280 Students and Examinations

### Attempt 1: Use groupby(), size(), merge(), and fillna()
```py
import pandas as pd

def students_and_examinations(students: pd.DataFrame, subjects: pd.DataFrame, examinations: pd.DataFrame) -> pd.DataFrame:
    eaxm_counts_df = examinations.groupby(['student_id', 'subject_name']).size().rename('attended_exams').reset_index()
    all_students_df = pd.merge(students, subjects, how='cross')
    merged_df = pd.merge(all_students_df, eaxm_counts_df, on=['student_id', 'subject_name'], how='outer')
    merged_df['attended_exams'].fillna(0, inplace=True)
    return merged_df.sort_values(['student_id', 'subject_name'])[['student_id', 'student_name', 'subject_name', 'attended_exams']]
```
- Runtime: 618 ms (Beats: 96.32%)
- Memory: 67.62 MB (Beats: 23.24%)

<br>
