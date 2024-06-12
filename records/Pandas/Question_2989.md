# [LeetCode Records](../../README.md) - Question 2989 Class Performance

### Attempt 1: Use max() and min()
```py
import pandas as pd

def class_performance(scores: pd.DataFrame) -> pd.DataFrame:
    scores['total'] = scores['assignment1'] + scores['assignment2'] + scores['assignment3']
    return pd.DataFrame({
        'difference_in_score': [scores['total'].max() - scores['total'].min()]
    })
```
- Runtime: 375 ms (Beats: 100.00%)
- Memory: 65.71 MB (Beats: 26.67%)

<br>
