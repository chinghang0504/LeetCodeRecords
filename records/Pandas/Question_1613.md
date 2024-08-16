# [LeetCode Records](../../README.md) - Question 1613 Find the Missing IDs

### Attempt 1: Use max() and isin()
```py
import pandas as pd

def find_missing_ids(customers: pd.DataFrame) -> pd.DataFrame:
    max_id = customers['customer_id'].max()

    all_ids = pd.DataFrame({
        'ids': np.arange(1, max_id)
    })

    return all_ids[~all_ids['ids'].isin(customers['customer_id'])].sort_values('ids')
```
- Runtime: 310 ms (Beats: 100.00%)
- Memory: 69.22 MB (Beats: 33.33%)

<br>
