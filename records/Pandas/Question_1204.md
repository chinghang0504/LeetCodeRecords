# [LeetCode Records](../../README.md) - Question 1204 Last Person to Fit in the Bus

### Attempt 1: Use cumsum() and tail()
```py
import pandas as pd

def last_passenger(queue: pd.DataFrame) -> pd.DataFrame:
    sorted_queue = queue.sort_values('turn')
    sorted_queue['total_weight'] = sorted_queue['weight'].cumsum()

    return sorted_queue[sorted_queue['total_weight'] <= 1000].tail(1)[['person_name']]
```
- Runtime: 398 ms (Beats: 86.97%)
- Memory: 70.56 MB (Beats: 12.26%)

<br>
