# [LeetCode Records](../../README.md) - Question 2887 Fill Missing Data

### Attempt 1: Use fillna()
```py
import pandas as pd

def fillMissingValues(products: pd.DataFrame) -> pd.DataFrame:
    products['quantity'] = products['quantity'].fillna(0)
    return products
```
- Runtime: 393 ms (Beats: 97.73%)
- Memory: 64.81 MB (Beats: 77.82%)

<br>
