# [LeetCode Records](../../README.md) - Question 1479 Sales by Day of the Week

### Attempt 1: Use pd.merge(), dt.strftime(), groupby(), sum(), fillna(), pivot(), rename_axis(), and reset_index()
```py
import pandas as pd

def sales_by_day(orders: pd.DataFrame, items: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(orders, items, on='item_id')
    merged_df['day_of_week'] = merged_df['order_date'].dt.strftime('%A')
    merged_df = merged_df.groupby(['item_category', 'day_of_week'])['quantity'].sum().reset_index()

    unique_items = pd.DataFrame({
        'item_category': items['item_category'].sort_values().unique()
    })
    day_of_weeks = pd.DataFrame({
        'day_of_week': ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
    })
    default_df = pd.merge(unique_items, day_of_weeks, how='cross')

    ans = pd.merge(default_df, merged_df, on=['item_category', 'day_of_week'], how='left').fillna(0)
    ans = ans.pivot(index='item_category', columns='day_of_week', values='quantity')
    ans = ans.rename_axis(None, axis=1).rename_axis('Category', axis=0).reset_index()
    return ans[['Category', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']]
```
- Runtime: 426 ms (Beats: 90.00%)
- Memory: 72.03 MB (Beats: 12.00%)

<br>
