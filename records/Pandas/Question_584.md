# [LeetCode Records](../../README.md) - Question 584 Find Customer Referee

### Attempt 1: 
```py
import pandas as pd

def find_customer_referee(customer: pd.DataFrame) -> pd.DataFrame:
    return customer[(customer['referee_id'].isna()) | (customer['referee_id'] != 2)]['name'].to_frame()
```
- Runtime: 529 ms (Beats: 95.52%)
- Memory: 64.97 MB (Beats: 90.55%)

<br>
