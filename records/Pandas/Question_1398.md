# [LeetCode Records](../../README.md) - Question 1398 Customers Who Bought Products A and B but Not C

### Attempt 1: Use isin()
```py
import pandas as pd

def find_customers(customers: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    product_A_customers_df = orders[orders['product_name'] == 'A']['customer_id']
    product_B_customers_df = orders[orders['product_name'] == 'B']['customer_id']
    product_C_customers_df = orders[orders['product_name'] == 'C']['customer_id']
    return customers[(customers['customer_id'].isin(product_A_customers_df)) & (customers['customer_id'].isin(product_B_customers_df)) & ~(customers['customer_id'].isin(product_C_customers_df))]
```
- Runtime: 541 ms (Beats: 93.33%)
- Memory: 65.15 MB (Beats: 86.67%)

<br>
