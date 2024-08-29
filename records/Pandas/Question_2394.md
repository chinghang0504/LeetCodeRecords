# [LeetCode Records](../../README.md) - Question 2394 Employees With Deductions

### Attempt 1: Use np.timedelta64(), apply(), math.ceil(), groupby(), sum(), pd.merge(), and fillna()
```py
import pandas as pd

def employees_with_deductions(employees: pd.DataFrame, logs: pd.DataFrame) -> pd.DataFrame:
    logs['working_time'] = (logs['out_time'] - logs['in_time']) / np.timedelta64(1, 'm')
    logs['working_time'] = logs['working_time'].apply(lambda x: math.ceil(x))
    working_time = logs.groupby('employee_id')['working_time'].sum().reset_index()

    employees['required_working_time'] = employees['needed_hours'] * 60

    merged_df = pd.merge(employees, working_time, on='employee_id', how='left').fillna(0)
    return merged_df[merged_df['working_time'] < merged_df['required_working_time']][['employee_id']]
```
- Runtime: 441 ms (Beats: 94.29%)
- Memory: 72.45 MB (Beats: 40.00%)

<br>
