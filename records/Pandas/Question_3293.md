# [LeetCode Records](../../README.md) - Question 3293 Calculate Product Final Price

### Attempt 1: Calculate the discount percentage
```py
import pandas as pd

def calculate_final_prices(products: pd.DataFrame, discounts: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(products, discounts, on='category', how='left').fillna(0)
    merged_df['final_price'] = merged_df['price'] * (100 - merged_df['discount']) / 100
    
    ans = merged_df.sort_values('product_id')
    return ans[['product_id', 'final_price', 'category']]
```
- Runtime: 335 ms (Beats: 86.21%)
- Memory: 70.70 MB (Beats: 20.69%)

<br>
