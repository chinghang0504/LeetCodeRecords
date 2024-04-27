# [LeetCode Records](../README.md) - Question 586 Customer Placing the Largest Number of Orders

### Attempt 1: 
```py
import pandas as pd

def largest_orders(orders: pd.DataFrame) -> pd.DataFrame:
    order_number_count = orders.groupby('customer_number').count().reset_index()
    max_order_number = order_number_count['order_number'].max()
    return order_number_count[order_number_count['order_number'] == max_order_number]['customer_number'].to_frame()
```
- Runtime: 538 ms (Beats: 93.09%)
- Memory: 66.55 MB (Beats: 17.63%)

<br>
