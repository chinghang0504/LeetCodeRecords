# [LeetCode Records](../../README.md) - Question 2889 Reshape Data: Pivot

### Attempt 1: Use pivot_table()
```py
import pandas as pd

def pivotTable(weather: pd.DataFrame) -> pd.DataFrame:
    return pd.pivot_table(weather, index='month', columns='city', values='temperature')
```
- Runtime: 462 ms (Beats: 97.15%)
- Memory: 67.14 MB (Beats: 20.96%)

<br>
