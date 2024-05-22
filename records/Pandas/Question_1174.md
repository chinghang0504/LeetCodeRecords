# [LeetCode Records](../../README.md) - Question 1174 Immediate Food Delivery II

### Attempt 1: Use groupby() and min()
```py
import pandas as pd

def immediate_food_delivery(delivery: pd.DataFrame) -> pd.DataFrame:
    first_order_df = delivery.groupby('customer_id')['order_date'].min().reset_index()
    merged_df = pd.merge(delivery, first_order_df, on=['customer_id', 'order_date'])
    same_day_df = merged_df[merged_df['order_date'] == merged_df['customer_pref_delivery_date']]
    return pd.DataFrame({
        'immediate_percentage': [round(len(same_day_df.index) / len(merged_df.index) * 100, 2)]
    })
```
- Runtime: 750 ms (Beats: 57.04%)
- Memory: 67.46 MB (Beats: 57.52%)

<br>
