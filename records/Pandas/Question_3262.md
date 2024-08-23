# [LeetCode Records](../../README.md) - Question 3262 Find Overlapping Shifts

### Attempt 1: Use pd.merge(), apply(), pd.to_datetime, and groupby()
```py
import pandas as pd

def isOverlapping(row):
    max_start_time = max(row['start_time_x'], row['start_time_y'])
    min_end_time = min(row['end_time_x'], row['end_time_y'])
    return int(max_start_time <= min_end_time)


def getNumOfOverlapping(df):
    merged_df = pd.merge(df, df, how='cross')
    merged_df['is_overlapping'] = merged_df.apply(isOverlapping, axis=1)
    return (merged_df['is_overlapping'].sum() - len(df)) // 2


def find_overlapping_shifts(employee_shifts: pd.DataFrame) -> pd.DataFrame:
    employee_shifts['start_time'] = pd.to_datetime(employee_shifts['start_time'])
    employee_shifts['end_time'] = pd.to_datetime(employee_shifts['end_time'])

    ans = employee_shifts.groupby('employee_id').apply(getNumOfOverlapping)
    ans = ans.rename('overlapping_shifts').reset_index()
    return ans[ans['overlapping_shifts'] > 0]
```
- Runtime: 486 ms (Beats: 20.00%)
- Memory: 71.22 MB (Beats: 20.00%)

<br>
