# [LeetCode Records](../../README.md) - Question 2329 Product Sales Analysis V

### Attempt 1: Use merge(), groupby(), and sum()
```py
import pandas as pd

def product_sales_analysis(sales: pd.DataFrame, product: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(sales, product, on='product_id')
    merged_df['spending'] = merged_df['quantity'] * merged_df['price']
    return merged_df.groupby('user_id')['spending'].sum().reset_index()[['user_id', 'spending']].sort_values('spending', ascending=False)
```
- Runtime: 434 ms (Beats: 100.00%)
- Memory: 67.63 MB (Beats: 57.89%)

<br>
