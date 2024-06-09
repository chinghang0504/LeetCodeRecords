# [LeetCode Records](../../README.md) - Question 2377 Sort the Olympic Table

### Attempt 1: Use sort_values()
```py
import pandas as pd

def sort_table(olympic: pd.DataFrame) -> pd.DataFrame:
    return olympic.sort_values(['gold_medals', 'silver_medals', 'bronze_medals', 'country'], ascending=[False, False, False, True])
```
- Runtime: 373 ms (Beats: 100.00%)
- Memory: 66.35 MB (Beats: 61.90%)

<br>
