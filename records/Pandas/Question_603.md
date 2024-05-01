# [LeetCode Records](../../README.md) - Question 603 Consecutive Available Seats

### Attempt 1: Use shift()
```py
import pandas as pd

def consecutive_available_seats(cinema: pd.DataFrame) -> pd.DataFrame:
    cinema = cinema.sort_values('seat_id')
    cinema['prev_free'] = cinema['free'].shift(1)
    cinema['next_free'] = cinema['free'].shift(-1)
    result = cinema[(cinema['free'] == 1) & ((cinema['prev_free'] == 1) | (cinema['next_free'] == 1))]
    return result[['seat_id']]
```
- Runtime: 571 ms (Beats: 78.64%)
- Memory: 65.56 MB (Beats: 78.64%)

<br>
