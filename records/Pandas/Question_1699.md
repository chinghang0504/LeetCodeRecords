# [LeetCode Records](../../README.md) - Question 1699 Number of Calls Between Two Persons

### Attempt 1: Use np.minimum(), np.maximum(), and groupby()
```py
import pandas as pd

def number_of_calls(calls: pd.DataFrame) -> pd.DataFrame:
    calls['person1'] = np.minimum(calls['from_id'], calls['to_id'])
    calls['person2'] = np.maximum(calls['from_id'], calls['to_id'])
    return calls.groupby(['person1', 'person2'])['duration'].agg(['count', 'sum']).rename(columns={'count': 'call_count', 'sum': 'total_duration'}).reset_index()
```
- Runtime: 408 ms (Beats: 98.04%)
- Memory: 67.28 MB (Beats: 82.35%)

<br>
