# [LeetCode Records](../../README.md) - Question 2886 Change Data Type

### Attempt 1: Use astype()
```py
import pandas as pd

def changeDatatype(students: pd.DataFrame) -> pd.DataFrame:
    return students.astype({'grade': 'int32'})
```
- Runtime: 390 ms (Beats: 98.47%)
- Memory: 65.39 MB (Beats: 60.16%)

<br>
