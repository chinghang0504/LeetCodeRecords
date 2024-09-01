# [LeetCode Records](../../README.md) - Question 

### Attempt 1: Use drop_duplicates() and sort_values()
```py
import pandas as pd
from datetime import datetime

def find_valid_users(purchases: pd.DataFrame, start_date: datetime, end_date: datetime, min_amount: int) -> pd.DataFrame:
    valid_purchases = purchases[purchases['amount'] >= min_amount]
    valid_purchases = valid_purchases[(valid_purchases['time_stamp'] >= start_date) & (valid_purchases['time_stamp'] <= end_date)]
    return valid_purchases[['user_id']].drop_duplicates().sort_values('user_id')
```
- Runtime: 359 ms (Beats: 100.00%)
- Memory: 71.19 MB (Beats: 100.00%)

<br>
