# [LeetCode Records](../../README.md) - Question 1164 Product Price at a Given Date

### Attempt 1: Use sort_values(), groupby(), last(), drop_duplicates(), merge(), and fillna()
```py
import pandas as pd

def price_at_given_date(products: pd.DataFrame) -> pd.DataFrame:
    valid_new_price_df = products[products['change_date'] <= np.datetime64('2019-08-16')]
    sorted_products_df = valid_new_price_df.sort_values(['product_id', 'change_date'])
    new_price_df = sorted_products_df.groupby('product_id')['new_price'].last().rename('price').reset_index()
    product_id_sr = products['product_id'].drop_duplicates()
    return pd.merge(new_price_df, product_id_sr, on='product_id', how='right').fillna(10)
```
- Runtime: 614 ms (Beats: 92.78%)
- Memory: 68.13 MB (Beats: 32.47%)

<br>
