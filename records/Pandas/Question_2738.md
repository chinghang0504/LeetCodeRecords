# [LeetCode Records](../../README.md) - Question 2738 Count Occurrences in Text

### Attempt 1: Use apply(), re.search(), and sum()
```py
import pandas as pd

def getCounts(row):
    if re.search("\sbull\s", row['content']):
        row['bull_count'] = 1
    else:
        row['bull_count'] = 0
        
    if re.search("\sbear\s", row['content']):
        row['bear_count'] = 1
    else:
        row['bear_count'] = 0
        
    return row


def count_occurrences(files: pd.DataFrame) -> pd.DataFrame:
    counts = files.apply(getCounts, axis=1)
    return pd.DataFrame({
        'word': ['bull', 'bear'],
        'count': [counts['bull_count'].sum(), counts['bear_count'].sum()]
    })
```
- Runtime: 924 ms (Beats: 5.04%)
- Memory: 70.00 MB (Beats: 7.46%)

<br>
