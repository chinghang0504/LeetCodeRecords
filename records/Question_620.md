# [LeetCode Records](../README.md) - Question 620 Not Boring Movies

### Attempt 1: 
```py
import pandas as pd

def not_boring_movies(cinema: pd.DataFrame) -> pd.DataFrame:
    selected_movies = cinema[(cinema['id'] % 2 == 1) & (cinema['description'] != 'boring')]
    return selected_movies.sort_values('rating', ascending=False)
```
- Runtime: 511 ms (Beats: 90.37%)
- Memory: 66.51 MB (Beats: 5.71%)

<br>
