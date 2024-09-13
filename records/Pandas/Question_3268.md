# [LeetCode Records](../../README.md) - Question 3268 Find Overlapping Shifts II

### Attempt 1: Use pd.merge() to get the combinations of shifts
```py
import pandas as pd

def get_overlaping_info(row):
    start_time = max(row['start_time_x'], row['start_time_y'])
    end_time = min(row['end_time_x'], row['end_time_y'])
    time_diff_in_min = (end_time - start_time) / np.timedelta64(1, 'm')
    is_overlapping = 1
    if time_diff_in_min <= 0:
        time_diff_in_min = 0
        is_overlapping = 0
    
    row['total_overlap_duration'] = time_diff_in_min
    row['max_overlapping_shifts'] = is_overlapping
    return row


def calculate_shift_overlaps(employee_shifts: pd.DataFrame) -> pd.DataFrame:
    employee_shifts['start_time'] = pd.to_datetime(employee_shifts['start_time'])
    employee_shifts['end_time'] = pd.to_datetime(employee_shifts['end_time'])
    employee_shifts_with_index = employee_shifts.reset_index()

    merged_df = pd.merge(employee_shifts_with_index, employee_shifts_with_index, on='employee_id')
    merged_df = merged_df[merged_df['index_x'] < merged_df['index_y']]
    merged_df = merged_df.apply(get_overlaping_info, axis=1)
    merged_df = merged_df.groupby('employee_id').agg({'max_overlapping_shifts': 'sum', 'total_overlap_duration': 'sum'}).reset_index()

    employees = pd.DataFrame({
        'employee_id': employee_shifts['employee_id'].unique()
    })
    ans = pd.merge(employees, merged_df, on='employee_id', how='left')
    ans = ans.fillna(0)
    ans['max_overlapping_shifts'] = ans['max_overlapping_shifts'].replace({1: 2, 0: 1})
    return ans.sort_values('employee_id')
```
- Runtime: 516 ms (Beats: 39.35%)
- Memory: 71.85 MB (Beats: 50.82%)

<br>
