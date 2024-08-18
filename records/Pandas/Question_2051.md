# [LeetCode Records](../../README.md) - Question 2051 The Category of Each Member in the Store

### Attempt 1: Use pd.merge(), groupby(), count(), and apply()
```py
import pandas as pd

def getCategory(row):
    if row['visit_count'] == 0:
        return 'Bronze'
    
    conversion_rate = 100 * row['purchase_count'] / row['visit_count']
    
    if conversion_rate >= 80:
        return 'Diamond'
    elif conversion_rate >= 50:
        return 'Gold'
    else:
        return 'Silver'


def find_categories(members: pd.DataFrame, visits: pd.DataFrame, purchases: pd.DataFrame) -> pd.DataFrame:
    purchase_records = pd.merge(visits, purchases, on='visit_id')

    purchase_counts = purchase_records.groupby('member_id')['visit_id'].count().rename('purchase_count').reset_index()
    visit_counts = visits.groupby('member_id')['visit_id'].count().rename('visit_count').reset_index()

    ans = pd.merge(members, visit_counts, on='member_id', how='left')
    ans = pd.merge(ans, purchase_counts, on='member_id', how='left').fillna(0)
    ans['category'] = ans.apply(getCategory, axis=1)
    
    return ans[['member_id', 'name', 'category']]
```
- Runtime: 451 ms (Beats: 96.77%)
- Memory: 71.74 MB (Beats: 54.84%)

<br>
