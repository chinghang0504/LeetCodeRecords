# [LeetCode Records](../../README.md) - Question 1565 Unique Orders and Customers Per Month

### Attempt 1: Use apply(), groupby(), and nunique()
```py
import pandas as pd

def datetimeToMonth(datetime):
    string = str(datetime)
    return string[0:4] + '-' + string[5:7]

def unique_orders_and_customers(orders: pd.DataFrame) -> pd.DataFrame:
    valid_orders = orders[orders['invoice'] > 20]
    valid_orders['month'] = valid_orders['order_date'].apply(datetimeToMonth)
    return valid_orders.groupby('month')[['order_id', 'customer_id']].nunique().rename(columns={'order_id': 'order_count', 'customer_id': 'customer_count'}).reset_index()
```
- Runtime: 558 ms (Beats: 100.00%)
- Memory: 68.17 MB (Beats: 14.71%)

<br>
