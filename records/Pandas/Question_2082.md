# [LeetCode Records](../../README.md) - Question 2082 The Number of Rich Customers

### Attempt 1: Use groupby, max(), and len()
```py
import pandas as pd

def count_rich_customers(store: pd.DataFrame) -> pd.DataFrame:
    max_amount_df = store.groupby('customer_id')['amount'].max()
    rich_count = len(max_amount_df[max_amount_df > 500].index)
    return pd.DataFrame({
        'rich_count': [rich_count]
    })
```
- Runtime: 366 ms (Beats: 100.00%)
- Memory: 66.29 MB (Beats: 25.90%)

<br>
