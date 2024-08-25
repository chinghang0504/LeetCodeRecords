# [LeetCode Records](../../README.md) - Question 580 Count Student Number in Departments

### Attempt 1: Use value_counts(), pd.merge(), fillna(), and sort_values()
```py
import pandas as pd

def count_students(student: pd.DataFrame, department: pd.DataFrame) -> pd.DataFrame:
    student_numbers = student['dept_id'].value_counts().rename('student_number').reset_index()

    ans = pd.merge(department, student_numbers, on='dept_id', how='left').fillna(0)
    return ans.sort_values(['student_number', 'dept_name'], ascending=[False, True])[['dept_name', 'student_number']]
```
- Runtime: 415 ms (Beats: 89.91%)
- Memory: 71.68 MB (Beats: 13.76%)

<br>
