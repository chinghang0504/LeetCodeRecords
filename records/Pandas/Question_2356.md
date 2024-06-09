# [LeetCode Records](../../README.md) - Question 2356 Number of Unique Subjects Taught by Each Teacher

### Attempt 1: Use groupby() and nunique()
```py
import pandas as pd

def count_unique_subjects(teacher: pd.DataFrame) -> pd.DataFrame:
    return teacher.groupby('teacher_id')['subject_id'].nunique().rename('cnt').reset_index()
```
- Runtime: 358 ms (Beats: 99.94%)
- Memory: 66.94 MB (Beats: 56.96%)

<br>
