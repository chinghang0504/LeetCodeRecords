# [LeetCode Records](../../README.md) - Question 1045 Customers Who Bought All Products

### Attempt 1: Use isin(), groupby(), nunique(), and len()
```py
import pandas as pd

def find_customers(customer: pd.DataFrame, product: pd.DataFrame) -> pd.DataFrame:
    related_customer = customer[customer['product_key'].isin(product['product_key'])]

    ans = related_customer.groupby('customer_id')['product_key'].nunique().rename('num_of_uniques').reset_index()
    return ans[ans['num_of_uniques'] == len(product)][['customer_id']]
```
- Runtime: 343 ms (Beats: 92.91%)
- Memory: 70.87 MB (Beats: 21.65%)

<br>
