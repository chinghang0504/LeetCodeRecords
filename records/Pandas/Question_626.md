# [LeetCode Records](../../README.md) - Question 626 Exchange Seats

### Attempt 1: Use apply() and loc[]
```py
import pandas as pd

def exchange_seats(seat: pd.DataFrame) -> pd.DataFrame:
    seat['id'] = seat['id'].apply(lambda x: x - 1 if x % 2 == 0 else x + 1)

    size = len(seat)
    if size % 2 == 1:
        seat.loc[size - 1, 'id'] = size
    
    return seat.sort_values('id')
```
- Runtime: 394 ms (Beats: 55.31%)
- Memory: 69.60 MB (Beats: 37.27%)

<br>
