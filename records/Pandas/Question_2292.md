# [LeetCode Records](../../README.md) - Question 2292 Products With Three or More Orders in Two Consecutive Years

### Attempt 1: Use dt.year, groupby(), count(), shift(), and drop_duplicates()
```py
import pandas as pd

def find_valid_products(orders: pd.DataFrame) -> pd.DataFrame:
    orders['year'] = orders['purchase_date'].dt.year
    order_counts = orders.groupby(['product_id', 'year'])['order_id'].count().rename('count').reset_index()
    order_counts[['next_year', 'next_count']] = order_counts.groupby('product_id')[['year', 'count']].shift(-1)

    valid_order_counts = order_counts[(order_counts['year'] + 1 == order_counts['next_year']) & (order_counts['count'] >= 3) & (order_counts['next_count'] >= 3)]
    return valid_order_counts[['product_id']].drop_duplicates()
```
- Runtime: 379 ms (Beats: 100.00%)
- Memory: 71.83 MB (Beats: 76.00%)

<br>
