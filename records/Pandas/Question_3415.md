# [LeetCode Records](../../README.md) - Question 3415 Find Products with Three Consecutive Digits

### Attempt 1: Use apply() to call a lambda function
```py
import pandas as pd


def find_products(products: pd.DataFrame) -> pd.DataFrame:
    products['exactly_three_digits'] = products['name'].apply(lambda name: sum(ch.isdigit() for ch in name))
    ans = products[products['exactly_three_digits'] == 3]
    ans = ans[['product_id', 'name']].sort_values('product_id')
    return ans
```
- Runtime: 435 ms (Beats: 100.00%)
- Memory: 66.96 MB (Beats: 100.00%)

<br>
