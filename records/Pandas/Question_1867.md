# [LeetCode Records](../../README.md) - Question 1867 Orders With Maximum Quantity Above Average

### Attempt 1: Use groupby(), mean(), and max()
```py
import pandas as pd

def orders_above_average(orders_details: pd.DataFrame) -> pd.DataFrame:
    average_orders = orders_details.groupby('order_id')['quantity'].mean().rename('avg').reset_index()
    max_avg = average_orders['avg'].max()

    max_orders = orders_details.groupby('order_id')['quantity'].max().rename('max').reset_index()

    return max_orders[max_orders['max'] > max_avg][['order_id']]
```
- Runtime: 395 ms (Beats: 92.86%)
- Memory: 70.86 MB (Beats: 53.57%)

<br>
