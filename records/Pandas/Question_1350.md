# [LeetCode Records](../../README.md) - Question 1350 Students With Invalid Departments

### Attempt 1: Use isin()
```py
import pandas as pd

def find_students(departments: pd.DataFrame, students: pd.DataFrame) -> pd.DataFrame:
    return students[~students['department_id'].isin(departments['id'])][['id', 'name']]
```
- Runtime: 532 ms (Beats: 99.22%)
- Memory: 66.56 MB (Beats: 45.14%)

<br>
