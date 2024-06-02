# [LeetCode Records](../../README.md) - Question 1445 Apples & Oranges

### Attempt 1: Use apply(), groupby(), and sum()
```py
import pandas as pd

def apples_oranges(sales: pd.DataFrame) -> pd.DataFrame:
    sales['diff'] = sales.apply(lambda row: row['sold_num'] if row['fruit'] == 'apples' else -row['sold_num'], axis=1)
    return sales.groupby('sale_date')['diff'].sum().reset_index()
```
- Runtime: 551 ms (Beats: 94.87%)
- Memory: 67.56 MB (Beats: 15.38%)

<br>
