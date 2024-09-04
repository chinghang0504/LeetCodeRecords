# [LeetCode Records](../../README.md) - Question 2253 Dynamic Unpivoting of a Table

### Attempt 1: Use pd.melt() to unpivot
```py
import pandas as pd

def find_valid_users(products: pd.DataFrame) -> pd.DataFrame:
    return pd.melt(products, id_vars=['product_id'], var_name='store', value_name='price').dropna()
```
- Runtime: 394 ms (Beats: 90.91%)
- Memory: 73.25 MB (Beats: 63.64%)

<br>
