# [LeetCode Records](../../README.md) - Question 2985 Calculate Compressed Mean

### Attempt 1: Use round()
```py
import pandas as pd

def compressed_mean(orders: pd.DataFrame) -> pd.DataFrame:
    orders['amount'] = orders['item_count'] * orders['order_occurrences']
    return pd.DataFrame({
        'average_items_per_order': [round(orders['amount'].sum() / orders['order_occurrences'].sum(), 2)]
    })
```
- Runtime: 356 ms (Beats: 100.00%)
- Memory: 64.96 MB (Beats: 78.79%)

<br>
