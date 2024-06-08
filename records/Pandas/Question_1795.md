# [LeetCode Records](../../README.md) - Question 1795 Rearrange Products Table

### Attempt 1: Use dropna(), assign(), and concat()
```py
import pandas as pd

def rearrange_products_table(products: pd.DataFrame) -> pd.DataFrame:
    store1_df = products[['product_id', 'store1']].dropna(subset='store1').assign(store='store1').rename(columns={'store1': 'price'})
    store2_df = products[['product_id', 'store2']].dropna(subset='store2').assign(store='store2').rename(columns={'store2': 'price'})
    store3_df = products[['product_id', 'store3']].dropna(subset='store3').assign(store='store3').rename(columns={'store3': 'price'})
    return pd.concat([store1_df, store2_df, store3_df])
```
- Runtime: 565 ms (Beats: 94.93%)
- Memory: 66.64 MB (Beats: 21.09%)

<br>
