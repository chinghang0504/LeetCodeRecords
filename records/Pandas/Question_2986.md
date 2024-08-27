# [LeetCode Records](../../README.md) - Question 2986 Find Third Transaction

### Attempt 1: Use sort_values(), groupby(), apply(), dropna(), and iloc[]
```py
import pandas as pd

def get_required_transaction(df):
    if len(df) < 3:
        return
    
    first_transaction_spend = df.iloc[0]['spend']
    second_transaction_spend = df.iloc[1]['spend']
    third_transaction_spend = df.iloc[2]['spend']
    if third_transaction_spend > first_transaction_spend and third_transaction_spend > second_transaction_spend:
        return df.iloc[2]


def find_third_transaction(transactions: pd.DataFrame) -> pd.DataFrame:
    sorted_transactions = transactions.sort_values(['user_id', 'transaction_date'])
    
    ans = sorted_transactions.groupby('user_id', group_keys=True).apply(get_required_transaction).dropna()

    if len(ans) != 0:
        return ans.rename(columns={'spend': 'third_transaction_spend', 'transaction_date': 'third_transaction_date'})
    else:
        return pd.DataFrame({
            'user_id': [],
            'third_transaction_spend': [],
            'third_transaction_date': [],
        })
```
- Runtime: 586 ms (Beats: 14.81%)
- Memory: 70.69 MB (Beats: 81.48%)

<br>
