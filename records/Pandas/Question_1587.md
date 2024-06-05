# [LeetCode Records](../../README.md) - Question 1587 Bank Account Summary II

### Attempt 1: Use groupby(), sum(), and merge()
```py
import pandas as pd

def account_summary(users: pd.DataFrame, transactions: pd.DataFrame) -> pd.DataFrame:
    balance_df = transactions.groupby('account')['amount'].sum().rename('balance').reset_index()
    valid_account_df = balance_df[balance_df['balance'] > 10000]
    return pd.merge(users, valid_account_df, on='account')[['name', 'balance']]
```
- Runtime: 445 ms (Beats: 100.00%)
- Memory: 67.82 MB (Beats: 25.64%)

<br>
