# [LeetCode Records](../../README.md) - Question 1484 Group Sold Products By The Date

### Attempt 1: Use groupby(), nunique(), agg(), join(), and merge()
```py
import pandas as pd

def categorize_products(activities: pd.DataFrame) -> pd.DataFrame:
    sorted_activities = activities.sort_values(['sell_date', 'product'])
    sorted_activities = sorted_activities.drop_duplicates()
    num_sold_df = sorted_activities.groupby('sell_date')['product'].nunique().rename('num_sold').reset_index()
    product_df = sorted_activities.groupby('sell_date')['product'].agg(lambda x: ','.join(x)).rename('products').reset_index()
    return pd.merge(num_sold_df, product_df, on='sell_date')
```
- Runtime: 415 ms (Beats: 95.05%)
- Memory: 67.97 MB (Beats: 23.74%)

<br>
