# [LeetCode Records](../../README.md) - Question 1068 Product Sales Analysis I

### Attempt 1: Use pd.merge()
```py
import pandas as pd

def sales_analysis(sales: pd.DataFrame, product: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(sales, product, on='product_id')
    return merged_df[['product_name', 'year', 'price']]

```
- Runtime: 591 ms (Beats: 98.06%)
- Memory: 69.29 MB (Beats: 8.78%)

<br>
