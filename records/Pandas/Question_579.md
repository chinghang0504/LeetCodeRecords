# [LeetCode Records](../../README.md) - Question 579 Find Cumulative Salary of an Employee

### Attempt 1: Use ~index.isin() to remove the most recent month
```py
import pandas as pd

def cumulative_salary(employee: pd.DataFrame) -> pd.DataFrame:
    ids = pd.DataFrame({
        'id': employee['id'].unique()
    })
    months = pd.DataFrame({
        'month': np.arange(1, 13)
    })
    default_df = pd.merge(ids, months, how='cross')

    sorted_employee = employee.sort_values(['id', 'month'])
    merged_df = pd.merge(default_df, sorted_employee, on=['id', 'month'], how='left').fillna(0)
    merged_df['prev_salary_1'] = merged_df.groupby('id')['salary'].shift(1).fillna(0)
    merged_df['prev_salary_2'] = merged_df.groupby('id')['salary'].shift(2).fillna(0)
    merged_df['salary'] = merged_df['salary'] + merged_df['prev_salary_1'] + merged_df['prev_salary_2']
    merged_df = merged_df.rename(columns={'salary': 'Salary'})[['id', 'month', 'Salary']]

    ans = employee[~employee.index.isin(employee.groupby('id')['month'].idxmax())][['id', 'month']]
    ans = pd.merge(ans, merged_df, on=['id', 'month'])
    return ans.sort_values(['id', 'month'], ascending=[True, False])
```
- Runtime: 452 ms (Beats: 76.71%)
- Memory: 71.88 MB (Beats: 38.36%)

<br>
