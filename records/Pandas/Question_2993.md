# [LeetCode Records](../../README.md) - Question 2993 Friday Purchases I

### Attempt 1: Use dt.year, dt.month, dt.day, dt.dayofweek, groupby(), and sum()
```py
import pandas as pd

def friday_purchases(purchases: pd.DataFrame) -> pd.DataFrame:
    purchases = purchases[purchases['purchase_date'].dt.year == 2023]
    purchases = purchases[purchases['purchase_date'].dt.month == 11]
    purchases = purchases[purchases['purchase_date'].dt.dayofweek == 4]

    ans = purchases.groupby('purchase_date')['amount_spend'].sum().rename('total_amount').reset_index()
    ans['week_of_month'] = ans['purchase_date'].dt.day // 7 + 1
    return ans[['week_of_month', 'purchase_date', 'total_amount']].sort_values('week_of_month')
```
- Runtime: 399 ms (Beats: 94.74%)
- Memory: 70.68 MB (Beats: 31.58%)

<br>
