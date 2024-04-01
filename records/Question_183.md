# [LeetCode Records](../README.md) - Question 183 Customers Who Never Order

### Attempt 1: Use merge() and isnull()
```py
import pandas as pd

def find_customers(customers: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    df = customers.merge(orders, left_on='id', right_on='customerId', how='outer')
    df = df[df['customerId'].isnull()]
    return pd.DataFrame({'Customers': df['name']})
```
- Runtime: 667 ms (Beats: 38.04%)
- Memory: 66.15 MB (Beats: 62.16%)

<br>
