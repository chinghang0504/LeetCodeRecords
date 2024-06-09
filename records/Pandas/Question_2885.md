# [LeetCode Records](../../README.md) - Question 2885 Rename Columns

### Attempt 1: Use rename()
```py
import pandas as pd

def renameColumns(students: pd.DataFrame) -> pd.DataFrame:
    return students.rename(columns={
        'id': 'student_id',
        'first': 'first_name',
        'last': 'last_name',
        'age': "age_in_years"
    })
```
- Runtime: 375 ms (Beats: 98.85%)
- Memory: 64.93 MB (Beats: 78.62%)

<br>
