# [LeetCode Records](../../README.md) - Question 2994 Friday Purchases II

### Attempt 1: Create a default dataframe first
```py
import pandas as pd

def friday_purchases(purchases: pd.DataFrame) -> pd.DataFrame:
    default_df = pd.DataFrame({
        'week_of_month': [1,2,3,4],
        'purchase_date': [
            np.datetime64('2023-11-03'),np.datetime64('2023-11-10'),np.datetime64('2023-11-17'),np.datetime64('2023-11-24')
        ]
    })

    merged_df = pd.merge(default_df, purchases, on='purchase_date', how='left').fillna(0)
    return merged_df.groupby(['week_of_month', 'purchase_date'])['amount_spend'].sum().rename('total_amount').reset_index()
```
- Runtime: 397 ms (Beats: 87.50%)
- Memory: 70.51 MB (Beats: 75.00%)

<br>
