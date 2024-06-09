# [LeetCode Records](../../README.md) - Question 2883 Drop Missing Data

### Attempt 1: Use dropna()
```py
import pandas as pd

def dropMissingData(students: pd.DataFrame) -> pd.DataFrame:
    return students.dropna(subset='name')
```
- Runtime: 388 ms (Beats: 98.63%)
- Memory: 65.93 MB (Beats: 52.21%)

<br>
