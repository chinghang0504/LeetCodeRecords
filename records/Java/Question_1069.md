# [LeetCode Records](../../README.md) - Question 1069 Product Sales Analysis II

### Attempt 1: Use groupby().sum()
```py
import pandas as pd

def sales_analysis(sales: pd.DataFrame, product: pd.DataFrame) -> pd.DataFrame:
    return sales.groupby('product_id')['quantity'].sum().rename("total_quantity").reset_index()

```
- Runtime: 564 ms (Beats: 93.75%)
- Memory: 68.19 MB (Beats: 52.50%)

<br>
