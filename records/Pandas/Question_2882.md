# [LeetCode Records](../../README.md) - Question 2882 Drop Duplicate Rows

### Attempt 1: Use drop_duplicates()
```py
import pandas as pd

def dropDuplicateEmails(customers: pd.DataFrame) -> pd.DataFrame:
    return customers.drop_duplicates('email')
```
- Runtime: 352 ms (Beats: 99.68%)
- Memory: 66.17 MB (Beats: 14.43%)

<br>
