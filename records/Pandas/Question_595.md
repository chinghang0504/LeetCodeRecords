# [LeetCode Records](../../README.md) - Question 595 Big Countries

### Attempt 1: 
```py
import pandas as pd

def big_countries(world: pd.DataFrame) -> pd.DataFrame:
    result = world[(world['area'] >= 3000000) | (world['population'] >= 25000000)]
    return result[['name', 'population', 'area']]
```
- Runtime: 500 ms (Beats: 94.66%)
- Memory: 67.11 MB (Beats: 84.69%)

<br>
