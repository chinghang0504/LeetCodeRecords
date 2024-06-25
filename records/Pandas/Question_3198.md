# [LeetCode Records](../../README.md) - Question 3198 Find Cities in Each State

### Attempt 1: Use sort_values(), groupby(), and apply()
```py
import pandas as pd

def find_cities(cities: pd.DataFrame) -> pd.DataFrame:
    sorted_cities = cities.sort_values(['state', 'city'])
    return sorted_cities.groupby('state')['city'].apply(lambda x: ', '.join(x)).rename('cities').reset_index()
```
- Runtime: 346 ms (Beats: 100.00%)
- Memory: 66.93 MB (Beats: 100.00%)

<br>
