# [LeetCode Records](../../README.md) - Question 2324 Product Sales Analysis IV

### Attempt 1: Use groupby(), sum(), pd.merge(), and max()
```py
import pandas as pd

def product_sales_analysis(sales: pd.DataFrame, product: pd.DataFrame) -> pd.DataFrame:
    total_sales = sales.groupby(['product_id', 'user_id'])['quantity'].sum().reset_index()

    total_amounts = pd.merge(total_sales, product, on='product_id')
    total_amounts['total_amount'] = total_amounts['quantity'] * total_amounts['price']

    max_total_amounts = total_amounts.groupby('user_id')['total_amount'].max().reset_index()

    return pd.merge(total_amounts, max_total_amounts, on=['user_id', 'total_amount'])[['user_id', 'product_id']]
```
- Runtime: 419 ms (Beats: 96.00%)
- Memory: 71.68 MB (Beats: 40.00%)

<br>
