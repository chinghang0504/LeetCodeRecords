# [LeetCode Records](../../README.md) - Question 1777 Product's Price for Each Store

### Attempt 1: Use merge()
```py
import pandas as pd

def products_price(products: pd.DataFrame) -> pd.DataFrame:
    store1_df = products[products['store'] == 'store1'].rename(columns={'price': 'store1'})[['product_id', 'store1']]
    store2_df = products[products['store'] == 'store2'].rename(columns={'price': 'store2'})[['product_id', 'store2']]
    store3_df = products[products['store'] == 'store3'].rename(columns={'price': 'store3'})[['product_id', 'store3']]
    merged_df = pd.merge(store1_df, store2_df, on='product_id', how='outer')
    return pd.merge(merged_df, store3_df, on='product_id', how='outer')
```
- Runtime: 483 ms (Beats: 96.67%)
- Memory: 66.87 MB (Beats: 63.33%)

<br>
