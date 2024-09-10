# [LeetCode Records](../../README.md) - Question 571 Find Median Given Frequency of Numbers

### Attempt 1: Use cumsum() to the cumulative frequency
```py
import pandas as pd

def median_frequency(numbers: pd.DataFrame) -> pd.DataFrame:
    sorted_numbers = numbers.sort_values('num')
    sorted_numbers['cumsum'] = sorted_numbers['frequency'].cumsum()

    number_size = sorted_numbers['frequency'].sum()
    target = (number_size + 1) // 2
    selected_numbers = sorted_numbers[sorted_numbers['cumsum'] >= target]

    if number_size % 2 == 0 and selected_numbers.iloc[0]['cumsum'] == target:
        median = (selected_numbers.iloc[0]['num'] + selected_numbers.iloc[1]['num']) / 2
    else:
        median = selected_numbers.iloc[0]['num']

    return pd.DataFrame({
        'median': [median]
    })
```
- Runtime: 341 ms (Beats: 73.21%)
- Memory: 69.96 MB (Beats: 25.89%)

<br>
