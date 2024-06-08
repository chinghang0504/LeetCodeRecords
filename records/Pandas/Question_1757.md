# [LeetCode Records](../../README.md) - Question 1757 Recyclable and Low Fat Products

### Attempt 1: 
```py
import pandas as pd

def find_products(products: pd.DataFrame) -> pd.DataFrame:
    return products[(products['low_fats'] == 'Y') & (products['recyclable'] == 'Y')][['product_id']]
```
- Runtime: 374 ms (Beats: 99.83%)
- Memory: 66.72 MB (Beats: 8.52%)

<br>
