# [LeetCode Records](../README.md) - Question 619 Biggest Single Number

### Attempt 1: 
```py
import pandas as pd

def biggest_single_number(my_numbers: pd.DataFrame) -> pd.DataFrame:
    count_numbers = my_numbers.groupby('num').value_counts().rename('count').reset_index()
    single_numbers = count_numbers[count_numbers['count'] == 1]
    return pd.DataFrame({
        'num': [single_numbers['num'].max()]
    })
```
- Runtime: 487 ms (Beats: 98.54%)
- Memory: 66.02 MB (Beats: 26.70%)

<br>
