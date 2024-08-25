# [LeetCode Records](../../README.md) - Question 3055 Top Percentile Fraud

### Attempt 1: Use sort_values(), groupby(), max(), and pd.merge()
```py
import pandas as pd

def top_percentile_fraud(fraud: pd.DataFrame) -> pd.DataFrame:
    sorted_fraud = fraud.sort_values(['state', 'fraud_score', 'policy_id'], ascending=[True, False, True])
    max_fraud = sorted_fraud.groupby('state')['fraud_score'].max().reset_index()
    return pd.merge(sorted_fraud, max_fraud, on=['state', 'fraud_score'])
```
- Runtime: 365 ms (Beats: 87.88%)
- Memory: 70.79 MB (Beats: 54.55%)

<br>
