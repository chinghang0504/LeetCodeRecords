# [LeetCode Records](../../README.md) - Question 2159 Order Two Columns Independently

### Attempt 1: Use sort_values()
```py
import pandas as pd

def order_two_columns(data: pd.DataFrame) -> pd.DataFrame:
    data['first_col'] = data['first_col'].sort_values(ignore_index=True)
    data['second_col'] = data['second_col'].sort_values(ascending=False, ignore_index=True)
    return data
```
- Runtime: 323 ms (Beats: 96.55%)
- Memory: 69.76 MB (Beats: 34.48%)

<br>
