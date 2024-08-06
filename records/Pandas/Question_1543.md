# [LeetCode Records](../../README.md) - Question 1543 Fix Product Name Format

### Attempt 1: Use apply(), strip(), lower(), dt.strftime(), groupby(), and count()
```py
import pandas as pd

def fix_name_format(sales: pd.DataFrame) -> pd.DataFrame:
    sales['product_name'] = sales['product_name'].apply(lambda name: name.strip().lower())
    sales['sale_date'] = sales['sale_date'].dt.strftime('%Y-%m')
    return sales.groupby(['product_name', 'sale_date'])['sale_id'].count().rename('total').reset_index().sort_values(['product_name', 'sale_date'])
```
- Runtime: 348 ms (Beats: 98.11%)
- Memory: 68.62 MB (Beats: 50.94%)

<br>
