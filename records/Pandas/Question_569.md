# [LeetCode Records](../../README.md) - Question 569 Median Employee Salary

### Attempt 1: Use apply() to return a data frame of the medians
```py
import pandas as pd

def get_median(df):
    size = len(df)
    half_index = size // 2
    start_index = half_index - 1 if size % 2 == 0 else half_index
    return df.iloc[start_index : half_index + 1, :]


def median_employee_salary(employee: pd.DataFrame) -> pd.DataFrame:
    sorted_employee = employee.sort_values(['company', 'salary', 'id'])
    return sorted_employee.groupby('company').apply(get_median).reset_index(drop=True)
```
- Runtime: 322 ms (Beats: 98.92%)
- Memory: 71.50 MB (Beats: 64.52%)

<br>
