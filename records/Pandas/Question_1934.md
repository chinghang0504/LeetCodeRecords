# [LeetCode Records](../../README.md) - Question 1934 Confirmation Rate

### Attempt 1: Use apply(), groupby(), agg(), np.round(), pd.merge(), and fillna()
```py
import pandas as pd

def confirmation_rate(signups: pd.DataFrame, confirmations: pd.DataFrame) -> pd.DataFrame:
    confirmations['result'] = confirmations['action'].apply(lambda action: 1 if action == 'confirmed' else 0)
    
    confirmation_result = confirmations.groupby('user_id').agg({'user_id': 'count', 'result': 'sum'})
    confirmation_result['confirmation_rate'] = np.round(confirmation_result['result'] / confirmation_result['user_id'], 2)
    confirmation_result = confirmation_result[['confirmation_rate']].reset_index()

    return pd.merge(signups, confirmation_result, on='user_id', how='left').fillna(0.0)[['user_id', 'confirmation_rate']]
```
- Runtime: 368 ms (Beats: 97.70%)
- Memory: 71.65 MB (Beats: 8.06%)

<br>
