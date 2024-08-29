# [LeetCode Records](../../README.md) - Question 1070 Product Sales Analysis III

### Attempt 1: Use groupby(), min(), and pd.merge()
```py
import pandas as pd

def sales_analysis(sales: pd.DataFrame, product: pd.DataFrame) -> pd.DataFrame:
    first_year_sales = sales.groupby('product_id')['year'].min().reset_index()

    ans = pd.merge(sales, first_year_sales, on=['product_id', 'year'])
    return ans.rename(columns={'year': 'first_year'})[['product_id', 'first_year', 'quantity', 'price']]
```
- Runtime: 360 ms (Beats: 99.10%)
- Memory: 73.36 MB (Beats: 13.69%)

<br>
