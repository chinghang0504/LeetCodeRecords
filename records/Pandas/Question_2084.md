# [LeetCode Records](../../README.md) - Question 2084 Drop Type 1 Orders for Customers With Type 0 Orders

### Attempt 1: Use isin() and concat()
```py
import pandas as pd

def drop_specific_orders(orders: pd.DataFrame) -> pd.DataFrame:
    type_0_orders_df = orders[orders['order_type'] == 0]
    type_0_customers_sr = type_0_orders_df['customer_id']
    other_orders_df = orders[~orders['customer_id'].isin(type_0_customers_sr)]
    return pd.concat([type_0_orders_df, other_orders_df])
```
- Runtime: 436 ms (Beats: 96.00%)
- Memory: 66.59 MB (Beats: 24.00%)

<br>
