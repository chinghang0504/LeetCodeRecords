# [LeetCode Records](../../README.md) - Question 1158 Market Analysis I

### Attempt 1: Use groupy(), count(), merge(), and fillna()
```py
import pandas as pd

def market_analysis(users: pd.DataFrame, orders: pd.DataFrame, items: pd.DataFrame) -> pd.DataFrame:
    valid_orders_df = orders[orders['order_date'].dt.year == 2019]
    order_counts_df = valid_orders_df.groupby('buyer_id')['order_id'].count().rename('orders_in_2019').reset_index()
    users_df = users.rename(columns={'user_id': 'buyer_id'})
    return pd.merge(users_df, order_counts_df, on='buyer_id', how='left').fillna(0)[['buyer_id', 'join_date', 'orders_in_2019']]
```
- Runtime: 666 ms (Beats: 97.34%)
- Memory: 68.30 MB (Beats: 39.53%)

<br>
