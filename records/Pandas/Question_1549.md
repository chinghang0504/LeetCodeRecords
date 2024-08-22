# [LeetCode Records](../../README.md) - Question 1549 The Most Recent Orders for Each Product

### Attempt 1: Use groupby(), max(), and pd.merge()
```py
import pandas as pd

def most_recent_orders(customers: pd.DataFrame, orders: pd.DataFrame, products: pd.DataFrame) -> pd.DataFrame:
    recent_order_dates = orders.groupby('product_id')['order_date'].max().reset_index()
    recent_order_dates = pd.merge(recent_order_dates, products, on='product_id')

    ans = pd.merge(orders, recent_order_dates, on=['product_id', 'order_date'])
    return ans.sort_values(['product_name', 'product_id', 'order_id'])[['product_name', 'product_id', 'order_id', 'order_date']]
```
- Runtime: 569 ms (Beats: 92.65%)
- Memory: 72.80 MB (Beats: 10.29%)

<br>
