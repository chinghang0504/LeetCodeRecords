# [LeetCode Records](../README.md) - Question 180 Consecutive Numbers

### Attempt 1: Use shift() twice
```py
import pandas as pd

def consecutive_numbers(logs: pd.DataFrame) -> pd.DataFrame:
    logs['num1'] = logs['num'].shift(1)
    logs['num2'] = logs['num'].shift(2)
    logs = logs[(logs['num'] == logs['num1']) & (logs['num'] == logs['num2'])]

    return pd.DataFrame({'ConsecutiveNums': logs['num'].unique()})
```
- Runtime: 596 ms (Beats: 77.83%)
- Memory: 66.20 MB (Beats: 39.09%)

<br>
