# [LeetCode Records](../../README.md) - Question 1083 Sales Analysis II

### Attempt 1: Use isin()
```py
import pandas as pd

def sales_analysis(product: pd.DataFrame, sales: pd.DataFrame) -> pd.DataFrame:
    S8_product_id = product[product['product_name'] == 'S8'].iloc[0]['product_id']
    iPhone_product_id = product[product['product_name'] == 'iPhone'].iloc[0]['product_id']
    S8_buyer_id = sales[sales['product_id'] == S8_product_id]['buyer_id'].drop_duplicates()
    iPhone_buyer_id = sales[sales['product_id'] == iPhone_product_id]['buyer_id'].drop_duplicates()
    return pd.DataFrame({
        'buyer_id': S8_buyer_id[~S8_buyer_id.isin(iPhone_buyer_id)]
    })
```
- Runtime: 605 ms (Beats: 98.61%)
- Memory: 68.72 MB (Beats: 48.61%)

<br>
