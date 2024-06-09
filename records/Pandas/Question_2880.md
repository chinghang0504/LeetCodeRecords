# [LeetCode Records](../../README.md) - Question 2880 Select Data

### Attempt 1: 
```py
import pandas as pd

def selectData(students: pd.DataFrame) -> pd.DataFrame:
    return students[students['student_id'] == 101][['name', 'age']]
```
- Runtime: 381 ms (Beats: 99.14%)
- Memory: 66.55 MB (Beats: 6.25%)

<br>
