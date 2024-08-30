# [LeetCode Records](../../README.md) - Question 2205 The Number of Users That Are Eligible for Discount

### Attempt 1: Use nunique()
```py
import pandas as pd
from datetime import datetime

def count_valid_users(purchases: pd.DataFrame, start_date: datetime, end_date: datetime, min_amount: int) -> pd.DataFrame:
    valid_purchases = purchases[(purchases['time_stamp'] >= start_date) & (purchases['time_stamp'] <= end_date)]
    valid_purchases = valid_purchases[valid_purchases['amount'] >= min_amount]
    return pd.DataFrame({
        'user_cnt': [valid_purchases['user_id'].nunique()]
    })
```
- Runtime: 389 ms (Beats: 100.00%)
- Memory: 71.44 MB (Beats: 100.00%)

<br>
