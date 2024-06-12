# [LeetCode Records](../../README.md) - Question 1831 Maximum Transaction Each Day

### Attempt 1: Use values, astype, groupby(), max(), and merge()
```py
import pandas as pd

def find_maximum_transaction(transactions: pd.DataFrame) -> pd.DataFrame:
    transactions['time_in_day'] = transactions['day'].values.astype('datetime64[D]')
    max_amount_sr = transactions.groupby('time_in_day')['amount'].max()
    return pd.merge(transactions, max_amount_sr, on=['time_in_day', 'amount'])[['transaction_id']].sort_values('transaction_id')
```
- Runtime: 443 ms (Beats: 97.37%)
- Memory: 68.20 MB (Beats: 7.89%)

<br>
