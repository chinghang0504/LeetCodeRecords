# [LeetCode Records](../../README.md) - Question 1205 Monthly Transactions II

### Attempt 1: Use dt.strftime, groupby(), agg(), pd.merge(), and fillna()
```py
import pandas as pd

def monthly_transactions(transactions: pd.DataFrame, chargebacks: pd.DataFrame) -> pd.DataFrame:
    transactions['month'] = transactions['trans_date'].dt.strftime('%Y-%m')
    approved_transactions = transactions[transactions['state'] == 'approved']
    transaction_ans = approved_transactions.groupby(['month', 'country']).agg(
        approved_count=('id', 'count'),
        approved_amount=('amount', 'sum')
    ).reset_index()

    chargebacks['month'] = chargebacks['trans_date'].dt.strftime('%Y-%m')
    merged_df = pd.merge(transactions[['id', 'country', 'amount']], chargebacks.rename(columns={'trans_id': 'id'}), on='id')
    chargeback_ans = merged_df.groupby(['month', 'country']).agg(
        chargeback_count=('id', 'count'),
        chargeback_amount=('amount', 'sum')
    ).reset_index()

    return pd.merge(transaction_ans, chargeback_ans, on=['month', 'country'], how='outer').fillna(0)
```
- Runtime: 527 ms (Beats: 91.30%)
- Memory: 72.32 MB (Beats: 19.57%)

<br>
