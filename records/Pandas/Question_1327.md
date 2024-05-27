# [LeetCode Records](../../README.md) - Question 1327 List the Products Ordered in a Period

### Attempt 1: Use groupy() and sum()
```py
import pandas as pd

def list_products(products: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    feb_orders_df = orders[(orders['order_date'] >= np.datetime64('2020-02-01')) & (orders['order_date'] <= np.datetime64('2020-02-29'))]
    total_units_df = feb_orders_df.groupby('product_id')['unit'].sum()
    at_least_100_df = total_units_df[total_units_df >= 100].reset_index()
    return pd.merge(products, at_least_100_df, on='product_id')[['product_name', 'unit']]
```
- Runtime: 608 ms (Beats: 93.49%)
- Memory: 67.96 MB (Beats: 34.32%)

<br>
