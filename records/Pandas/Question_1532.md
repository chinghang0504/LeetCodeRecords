# [LeetCode Records](../../README.md) - Question 1532 The Most Recent Three Orders

### Attempt 1: Use pd.merge(), groupby(), and head()
```py
import pandas as pd

def recent_three_orders(customers: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    merged_orders = pd.merge(customers, orders, on='customer_id').rename(columns={'name': 'customer_name'})

    sorted_orders = merged_orders.sort_values(['customer_name', 'customer_id', 'order_date'], ascending=[True, True, False])

    ans = sorted_orders.groupby('customer_id').head(3)

    return ans[['customer_name', 'customer_id', 'order_id', 'order_date']]
```
- Runtime: 430 ms (Beats: 98.39%)
- Memory: 72.09 MB (Beats: 32.26%)

<br>
