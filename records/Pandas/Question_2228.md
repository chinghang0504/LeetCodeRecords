# [LeetCode Records](../../README.md) - Question 2228 Users With Two Purchases Within Seven Days

### Attempt 1: Use groupby(), count(), isin(), pd.merge(), np.timedelta64(), drop_duplicates(), and sort_values()
```py
import pandas as pd

def find_valid_users(purchases: pd.DataFrame) -> pd.DataFrame:
    purchase_counts = purchases.groupby('user_id')['purchase_id'].count().rename('count').reset_index()
    selected_purchases = purchases[purchases['user_id'].isin(purchase_counts['user_id'])]

    merged_df = pd.merge(selected_purchases, selected_purchases, how='cross')
    merged_df = merged_df[(merged_df['user_id_x'] == merged_df['user_id_y']) & (merged_df['purchase_id_x'] != merged_df['purchase_id_y'])]
    merged_df = merged_df[merged_df['purchase_date_x'] <= merged_df['purchase_date_y']]
    merged_df['diff'] = merged_df['purchase_date_y'] - merged_df['purchase_date_x']

    ans = merged_df[merged_df['diff'] <= np.timedelta64(7, 'D')]
    ans = ans[['user_id_x']].rename(columns={'user_id_x': 'user_id'})
    return ans.drop_duplicates().sort_values('user_id')
```
- Runtime: 425 ms (Beats: 65.38%)
- Memory: 104.03 MB (Beats: 7.69%)

<br>
