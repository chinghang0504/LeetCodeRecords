# [LeetCode Records](../../README.md) - Question 3118 Friday Purchase III

### Attempt 1: Use dt.year, dt.month, dt.dayofweek, dt.day, pd.merge(), pd.concat(), groupby(), and sum()
```py
import pandas as pd

def friday_purchases(purchases: pd.DataFrame, users: pd.DataFrame) -> pd.DataFrame:
    selected_purchases = purchases[(purchases['purchase_date'].dt.year == 2023) & (purchases['purchase_date'].dt.month == 11) & (purchases['purchase_date'].dt.dayofweek == 4)]
    selected_purchases['week_of_month'] = (selected_purchases['purchase_date'].dt.day - 1) // 7 + 1
    
    selected_users = users[(users['membership'] == 'Premium') | (users['membership'] == 'VIP')]

    merged_df = pd.merge(selected_purchases, selected_users, on='user_id')[['amount_spend', 'week_of_month', 'membership']]
    zero_purchases = pd.DataFrame({
        'amount_spend': [0, 0, 0, 0, 0, 0, 0, 0],
        'week_of_month': [1, 2, 3, 4, 1, 2, 3, 4],
        'membership': ['Premium','Premium','Premium','Premium','VIP','VIP','VIP','VIP']
    })
    merged_df = pd.concat([merged_df, zero_purchases], ignore_index=True)

    ans = merged_df.groupby(['membership', 'week_of_month'])['amount_spend'].sum().rename('total_amount').reset_index()
    return ans.sort_values(['week_of_month', 'membership'])[['week_of_month', 'membership', 'total_amount']]
```
- Runtime: 415 ms (Beats: 92.86%)
- Memory: 71.22 MB (Beats: 58.93%)

<br>
