# [LeetCode Records](../README.md) - Question 596 Classes More Than 5 Students

### Attempt 1: 
```py
import pandas as pd

def find_classes(courses: pd.DataFrame) -> pd.DataFrame:
    counts = courses.groupby('class').count().reset_index()
    result = counts[counts['student'] >= 5]
    return result['class'].to_frame()
```
- Runtime: 469 ms (Beats: 99.52%)
- Memory: 67.46 MB (Beats: 5.28%)

<br>
