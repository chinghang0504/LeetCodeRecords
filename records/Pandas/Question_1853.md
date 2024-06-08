# [LeetCode Records](../../README.md) - Question 1853 Convert Date Format

### Attempt 1: Use apply() and strftime()
```py
import pandas as pd

def convert_date_format(days: pd.DataFrame) -> pd.DataFrame:
    days['day'] = days['day'].apply(lambda x: x.strftime("%A, %B %-d, %Y"))
    return days
```
- Runtime: 417 ms (Beats: 100.00%)
- Memory: 66.36 MB (Beats: 26.67%)

<br>
