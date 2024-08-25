# [LeetCode Records](../../README.md) - Question 1193 Monthly Transactions I

### Attempt 1: Use dt.strftime(), groupby(), agg(), pd.merge(), and fillna()
```py
import pandas as pd

def monthly_transactions(transactions: pd.DataFrame) -> pd.DataFrame:
    transactions['month'] = transactions['trans_date'].dt.strftime('%Y-%m')

    total_transactions = transactions.groupby(['month', 'country'], dropna=False).agg({'id': 'count', 'amount': 'sum'}).rename(columns={'id': 'trans_count', 'amount': 'trans_total_amount'}).reset_index()

    approved_transactions = transactions[transactions['state'] == 'approved']
    approved_transactions = approved_transactions.groupby(['month', 'country'], dropna=False).agg({'id': 'count', 'amount': 'sum'}).rename(columns={'id': 'approved_count', 'amount': 'approved_total_amount'}).reset_index()

    ans = pd.merge(total_transactions, approved_transactions, on=['month', 'country'], how='outer')
    ans[['approved_count', 'approved_total_amount']] = ans[['approved_count', 'approved_total_amount']].fillna(0)
    return ans[['month', 'country', 'trans_count', 'approved_count', 'trans_total_amount', 'approved_total_amount']]
```
- Runtime: 483 ms (Beats: 77.01%)
- Memory: 71.88 MB (Beats: 37.57%)

<br>
