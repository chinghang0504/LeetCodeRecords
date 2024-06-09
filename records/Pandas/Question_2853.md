# [LeetCode Records](../../README.md) - Question 2853 Highest Salaries Difference

### Attempt 1: Use groupby(), max(), and abs()
```py
import pandas as pd

def salaries_difference(salaries: pd.DataFrame) -> pd.DataFrame:
    max_salaries_sr = salaries.groupby('department')['salary'].max()
    return pd.DataFrame({
        'salary_difference': [abs(max_salaries_sr['Engineering'] - max_salaries_sr['Marketing'])]
    })
```
- Runtime: 353 ms (Beats: 94.74%)
- Memory: 66.16 MB (Beats: 10.53%)

<br>
