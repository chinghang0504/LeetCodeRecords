# [LeetCode Records](../../README.md) - Question 2252 Dynamic Pivoting of a Table

### Attempt 1: Use pivot() to change the index, columns, and values
```py
import pandas as pd

def dynamic_pivoting_table(products: pd.DataFrame) -> pd.DataFrame:
    ans = products.pivot(index='product_id', columns='store', values='price')
    ans.columns.name = None
    return ans.reset_index()
```
- Runtime: 384 ms (Beats: 94.12%)
- Memory: 72.98 MB (Beats: 82.35%)

<br>
