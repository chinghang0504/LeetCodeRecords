# [LeetCode Records](../../README.md) - Question 2314 The First Day of the Maximum Recorded Degree in Each City

### Attempt 1: Use loc(), groupby(), and idxmax()
```py
import pandas as pd

def find_the_first_day(weather: pd.DataFrame) -> pd.DataFrame:
    sorted_weather = weather.sort_values(['city_id', 'day'])
    return sorted_weather.loc[sorted_weather.groupby('city_id')['degree'].idxmax()].sort_values('city_id')
```
- Runtime: 367 ms (Beats: 100.00%)
- Memory: 71.39 MB (Beats: 55.56%)

<br>
