# [LeetCode Records](../../README.md) - Question 177 Nth Highest Salary

### Attempt 1: Convert the Series to NumPy
```py
import pandas as pd

def nth_highest_salary(employee: pd.DataFrame, N: int) -> pd.DataFrame:
    salary = employee['salary'].to_numpy()
    salary = np.unique(salary)
    return pd.DataFrame({f'getNthHighestSalary({N})': [None if salary.shape[0] < N or N < 1 else salary[-N]]})
```
- Runtime: 584 ms (Beats: 63.49%)
- Memory: 65.77 MB (Beats: 69.89%)

<br>
