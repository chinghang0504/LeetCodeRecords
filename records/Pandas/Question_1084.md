# [LeetCode Records](../../README.md) - Question 1084 Sales Analysis III

### Attempt 1: Use isin()
```py
import pandas as pd

def sales_analysis(product: pd.DataFrame, sales: pd.DataFrame) -> pd.DataFrame:
    invalid_product_id = sales[(sales['sale_date'] < np.datetime64('2019-01-01')) | (sales['sale_date'] > np.datetime64('2019-03-31'))]['product_id']
    valid_product_id_df = sales[~sales['product_id'].isin(invalid_product_id)].drop_duplicates('product_id')
    return pd.merge(valid_product_id_df, product, on='product_id')[['product_id', 'product_name']]
```
- Runtime: 651 ms (Beats: 93.44%)
- Memory: 69.80 MB (Beats: 6.88%)

<br>
