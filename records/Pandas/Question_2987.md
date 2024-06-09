# [LeetCode Records](../../README.md) - Question 2987 Find Expensive Cities

### Attempt 1: Use mean() and groupby()
```py
import pandas as pd

def find_expensive_cities(listings: pd.DataFrame) -> pd.DataFrame:
    national_average = listings['price'].mean()
    city_mean_df = listings.groupby('city')['price'].mean().reset_index()
    return city_mean_df[city_mean_df['price'] > national_average].sort_values('city')[['city']]
```
- Runtime: 380 ms (Beats: 100.00%)
- Memory: 66.46 MB (Beats: 61.29%)

<br>
