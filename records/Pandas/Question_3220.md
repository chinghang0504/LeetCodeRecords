# [LeetCode Records](../../README.md) - Question 3220 Odd and Even Transactions

### Attempt 1: Use groupby(), sum(), and pd.merge()
```py
import pandas as pd

def sum_daily_odd_even(transactions: pd.DataFrame) -> pd.DataFrame:
    odd_transactions = transactions[transactions['amount'] % 2 == 1]
    odd_sum = odd_transactions.groupby('transaction_date')['amount'].sum().rename('odd_sum').reset_index()

    even_transactions = transactions[transactions['amount'] % 2 == 0]
    even_sum = even_transactions.groupby('transaction_date')['amount'].sum().rename('even_sum').reset_index()

    return pd.merge(odd_sum, even_sum, on='transaction_date', how='outer').fillna(0).sort_values('transaction_date')
```
- Runtime: 352 ms (Beats: 82.18%)
- Memory: 70.79 MB (Beats: 29.70%)

<br>
