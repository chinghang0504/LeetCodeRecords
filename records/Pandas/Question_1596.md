# [LeetCode Records](../../README.md) - Question 1596 The Most Frequently Ordered Products for Each Customer

### Attempt 1: Use groupy(), count(), max(), and pd.merge()
```py
import pandas as pd

def most_frequently_products(customers: pd.DataFrame, orders: pd.DataFrame, products: pd.DataFrame) -> pd.DataFrame:
    order_counts = orders.groupby(['customer_id', 'product_id'])['order_id'].count().rename('count').reset_index()

    max_counts = order_counts.groupby('customer_id')['count'].max().reset_index()
    max_counts = pd.merge(order_counts, max_counts, on=['customer_id', 'count'])

    return pd.merge(max_counts, products, on='product_id')[['customer_id', 'product_id', 'product_name']]
```
- Runtime: 549 ms (Beats: 100.00%)
- Memory: 72.42 MB (Beats: 34.00%)

<br>
