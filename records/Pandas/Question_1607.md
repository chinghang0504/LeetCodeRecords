# [LeetCode Records](../../README.md) - Question 1607 Sellers With No Sales

### Attempt 1: Use isin()
```py
import pandas as pd

def sellers_with_no_sales(customer: pd.DataFrame, orders: pd.DataFrame, seller: pd.DataFrame) -> pd.DataFrame:
    seller_2020_df = orders_2020_df = orders[orders['sale_date'].dt.year == 2020]['seller_id']
    return seller[~seller['seller_id'].isin(seller_2020_df)][['seller_name']].sort_values('seller_name')
```
- Runtime: 557 ms (Beats: 98.21%)
- Memory: 66.95 MB (Beats: 46.43%)

<br>
