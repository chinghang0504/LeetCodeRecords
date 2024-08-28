# [LeetCode Records](../../README.md) - Question 1843 Suspicious Bank Accounts

### Attempt 1: Use dt.year, dt.month, groupby(), sum(), pd.merge(), apply(), shift(), and len()
```py
import pandas as pd

def isSuspicious(df):
    df[['next_month', 'next_sum', 'next_is_exceeded']] = df[['month', 'sum', 'is_exceeded']].shift(-1)
    df = df[df['next_month'] - 1 == df['month']]
    df = df[df['next_is_exceeded'] & df['is_exceeded']]
    return len(df) != 0


def suspicious_bank_accounts(accounts: pd.DataFrame, transactions: pd.DataFrame) -> pd.DataFrame:
    income_transactions = transactions[transactions['type'] == 'Creditor']
    income_transactions['month'] = income_transactions['day'].dt.year * 12 + income_transactions['day'].dt.month
    income_transactions = income_transactions.groupby(['account_id', 'month'])['amount'].sum().rename('sum').reset_index()
    
    merged_df = pd.merge(accounts, income_transactions, on='account_id')
    merged_df['is_exceeded'] = merged_df['sum'] > merged_df['max_income']

    ans = merged_df.groupby('account_id').apply(isSuspicious).rename('is_suspicious').reset_index()
    return ans[ans['is_suspicious']][['account_id']]
```
- Runtime: 1699 ms (Beats: 5.17%)
- Memory: 72.20 MB (Beats: 77.59%)

<br>
