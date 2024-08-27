# [LeetCode Records](../../README.md) - Question 1555 Bank Account Summary

### Attempt 1: Use pd.concat(), groupby(), sum(), pd.merge(), and apply()
```py
import pandas as pd

def bank_account_summary(users: pd.DataFrame, transactions: pd.DataFrame) -> pd.DataFrame:
    original_credits = users[['user_id', 'credit']]
    paid_by_transactions = transactions[['paid_by', 'amount']].rename(columns={'paid_by': 'user_id', 'amount': 'credit'})
    paid_by_transactions['credit'] = -paid_by_transactions['credit']
    paid_to_transactions = transactions[['paid_to', 'amount']].rename(columns={'paid_to': 'user_id', 'amount': 'credit'})

    new_credits = pd.concat([original_credits, paid_by_transactions, paid_to_transactions])
    new_credits = new_credits.groupby('user_id')['credit'].sum().reset_index()

    ans = pd.merge(users[['user_id', 'user_name']], new_credits, on='user_id')
    ans['credit_limit_breached'] = ans['credit'].apply(lambda credit: 'No' if credit >= 0 else 'Yes')
    return ans
```
- Runtime: 388 ms (Beats: 100.00%)
- Memory: 70.87 MB (Beats: 25.71%)

<br>
