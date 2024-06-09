# [LeetCode Records](../../README.md) - Question 2879 Display the First Three Rows

### Attempt 1: Use iloc
```py
import pandas as pd

def selectFirstRows(employees: pd.DataFrame) -> pd.DataFrame:
    return employees.iloc[0:3]
```
- Runtime: 371 ms (Beats: 99.08%)
- Memory: 65.74 MB (Beats: 11.67%)

<br>
