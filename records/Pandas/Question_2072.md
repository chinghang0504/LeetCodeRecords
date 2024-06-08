# [LeetCode Records](../../README.md) - Question 2072 The Winner University

### Attempt 1: 
```py
import pandas as pd

def find_winner(new_york: pd.DataFrame, california: pd.DataFrame) -> pd.DataFrame:
    new_york_num = len(new_york[new_york['score'] >= 90].index)
    california_num = len(california[california['score'] >= 90].index)

    if new_york_num > california_num:
        output = 'New York University'
    elif california_num > new_york_num:
        output = 'California University'
    else:
        output = 'No Winner'

    return pd.DataFrame({
        'winner':  [output]
    })
```
- Runtime: 378 ms (Beats: 100.00%)
- Memory: 65.78 MB (Beats: 43.75%)

<br>
