# [LeetCode Records](../../README.md) - Question 2668 Find Latest Salaries

### Attempt 1: Use groupby(), max(), and merge()
```py
import pandas as pd

def find_latest_salaries(salary: pd.DataFrame) -> pd.DataFrame:
    max_salary_df = salary.groupby('emp_id')['salary'].max().reset_index()
    return pd.merge(salary, max_salary_df, on=['emp_id', 'salary']).sort_values('emp_id')
```
- Runtime: 446 ms (Beats: 100.00%)
- Memory: 67.19 MB (Beats: 9.52%)

<br>
