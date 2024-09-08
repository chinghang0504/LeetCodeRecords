# [LeetCode Records](../../README.md) - Question 2474 Customers With Strictly Increasing Purchases

### Attempt 1: Use all() to get customer id which all the conditions are true
```py
import pandas as pd

def find_specific_customers(orders: pd.DataFrame) -> pd.DataFrame:
    orders['year'] = orders['order_date'].dt.year

    total_amounts = orders.groupby(['customer_id', 'year'])['price'].sum().rename('total_amount').reset_index()
    order_counts = total_amounts['customer_id'].value_counts().rename('count').reset_index()
    order_counts = order_counts[order_counts['count'] == 1]

    total_amounts[['next_year', 'next_total_amount']] = total_amounts.groupby('customer_id')[['year', 'total_amount']].shift(-1)
    total_amounts = total_amounts.dropna()
    total_amounts['is_next_year'] = total_amounts['next_year'] - total_amounts['year'] == 1
    total_amounts['is_increased'] = total_amounts['next_total_amount'] > total_amounts['total_amount']

    ans = total_amounts.groupby('customer_id')[['is_next_year', 'is_increased']].all().reset_index()
    ans = ans[ans['is_next_year'] & ans['is_increased']]
    ans = ans[['customer_id']]
    return pd.concat([ans, order_counts[['customer_id']]])
```
- Runtime: 469 ms (Beats: 77.27%)
- Memory: 72.13 MB (Beats: 36.36%)

<br>
