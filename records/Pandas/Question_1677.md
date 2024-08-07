# [LeetCode Records](../../README.md) - Question 1677 Product's Worth Over Invoices

### Attempt 1: Use groupby(), sum(), and pd.merge()
```py
import pandas as pd

def analyze_products(product: pd.DataFrame, invoice: pd.DataFrame) -> pd.DataFrame:
    sum_df = invoice.groupby('product_id')[['rest', 'paid', 'canceled', 'refunded']].sum().reset_index()
    return pd.merge(sum_df, product, on='product_id', how='outer').fillna(0)[['name', 'rest', 'paid', 'canceled', 'refunded']].sort_values('name')
```
- Runtime: 391 ms (Beats: 97.73%)
- Memory: 71.18 MB (Beats: 38.64%)

<br>
