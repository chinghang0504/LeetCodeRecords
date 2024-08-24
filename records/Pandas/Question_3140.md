# [LeetCode Records](../../README.md) - Question 3140 Consecutive Available Seats II

### Attempt 1: Use min(), max(), pd.concat(), and shift()
```py
import pandas as pd

def consecutive_available_seats(cinema: pd.DataFrame) -> pd.DataFrame:
    dummy_cinema = pd.DataFrame({'seat_id': [cinema['seat_id'].min() - 1, cinema['seat_id'].max() + 1], 'free': [0, 0]})

    sorted_cinema = pd.concat([dummy_cinema, cinema], ignore_index=True).sort_values('seat_id')
    sorted_cinema = sorted_cinema[sorted_cinema['free'] == 0]
    sorted_cinema['next_seat_id'] = sorted_cinema['seat_id'].shift(-1)
    sorted_cinema['len'] = sorted_cinema['next_seat_id'] - sorted_cinema['seat_id'] - 1

    max_len = sorted_cinema['len'].max()
    ans = sorted_cinema[sorted_cinema['len'] == max_len]
    ans['first_seat_id'] = ans['seat_id'] + 1
    ans['last_seat_id'] = ans['first_seat_id'] + max_len - 1
    ans['consecutive_seats_len'] = max_len
    return ans[['first_seat_id', 'last_seat_id', 'consecutive_seats_len']]
```
- Runtime: 380 ms (Beats: 100.00%)
- Memory: 69.85 MB (Beats: 63.64%)

<br>
