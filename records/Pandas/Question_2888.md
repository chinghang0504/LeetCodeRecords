# [LeetCode Records](../../README.md) - Question 2888 Reshape Data: Concatenate

### Attempt 1: Use concat()
```py
import pandas as pd

def concatenateTables(df1: pd.DataFrame, df2: pd.DataFrame) -> pd.DataFrame:
    return pd.concat([df1, df2])
```
- Runtime: 385 ms (Beats: 99.50%)
- Memory: 66.12 MB (Beats: 7.44%)

<br>
