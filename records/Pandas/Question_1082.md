# [LeetCode Records](../../README.md) - Question 1082 Sales Analysis I

### Attempt 1: Use groupy() and sum()
```py
import pandas as pd

def sales_analysis(product: pd.DataFrame, sales: pd.DataFrame) -> pd.DataFrame:
    total_sales_df = sales.groupby('seller_id')['price'].sum()
    max_total_sales = total_sales_df.max()
    return total_sales_df[total_sales_df == max_total_sales].reset_index()[['seller_id']]
```
- Runtime: 586 ms (Beats: 96.00%)
- Memory: 67.97 MB (Beats: 73.33%)

<br>
