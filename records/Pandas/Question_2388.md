# [LeetCode Records](../../README.md) - Question 2388 Change Null Values in a Table to the Previous Value

### Attempt 1: Use fillna()
```py
import pandas as pd

def change_null_values(coffee_shop: pd.DataFrame) -> pd.DataFrame:
    return coffee_shop.fillna(method='ffill')
```
- Runtime: 324 ms (Beats: 100.00%)
- Memory: 69.66 MB (Beats: 6.67%)

<br>
