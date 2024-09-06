# [LeetCode Records](../../README.md) - Question 1159 Market Analysis II

### Attempt 1: Use rank() to get the second sold items
```py
import pandas as pd

def market_analysis(users: pd.DataFrame, orders: pd.DataFrame, items: pd.DataFrame) -> pd.DataFrame:
    users = users.rename(columns={'user_id': 'seller_id'})

    merged_df = pd.merge(orders, users, on='seller_id')
    merged_df = pd.merge(merged_df, items, on='item_id')
    merged_df['rank'] = merged_df.groupby('seller_id')['order_date'].rank()
    merged_df = merged_df[merged_df['rank'] == 2]
    merged_df['2nd_item_fav_brand'] = merged_df.apply(lambda row: 'yes' if row['favorite_brand'] == row['item_brand'] else 'no', axis=1)
    merged_df = merged_df[['seller_id', '2nd_item_fav_brand']]

    return pd.merge(users[['seller_id']], merged_df, on='seller_id', how='left').fillna('no')
```
- Runtime: 470 ms (Beats: 87.50%)
- Memory: 71.70 MB (Beats: 69.64%)

<br>
