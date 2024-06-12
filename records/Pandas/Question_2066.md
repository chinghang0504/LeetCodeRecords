# [LeetCode Records](../../README.md) - Question 2066 Account Balance

### Attempt 1: Use apply(), groupby(), and cumsum()
```py
import pandas as pd


def getBalance(row):
    return row['amount'] if row['type'] == 'Deposit' else -row['amount']


def account_balance(transactions: pd.DataFrame) -> pd.DataFrame:
    transactions = transactions.sort_values('day')
    transactions['change'] = transactions.apply(getBalance, axis=1)
    transactions['balance'] = transactions.groupby('account_id')['change'].cumsum()
    return transactions[['account_id', 'day', 'balance']].sort_values(['account_id', 'day'])
```
- Runtime: 398 ms (Beats: 100.00%)
- Memory: 67.90 MB (Beats: 52.17%)

<br>
