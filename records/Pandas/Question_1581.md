# [LeetCode Records](../../README.md) - Question 1581 Customer Who Visited but Did Not Make Any Transactions

### Attempt 1: Use isin(), groupby() and count()
```py
import pandas as pd

def find_customers(visits: pd.DataFrame, transactions: pd.DataFrame) -> pd.DataFrame:
    visit_without_transactions_df = visits[~visits['visit_id'].isin(transactions['visit_id'])]
    return visit_without_transactions_df.groupby('customer_id')['visit_id'].count().rename('count_no_trans').reset_index()
```
- Runtime: 633 ms (Beats: 96.36%)
- Memory: 65.90 MB (Beats: 94.30%)

<br>
