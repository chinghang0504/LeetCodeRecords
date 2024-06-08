# [LeetCode Records](../../README.md) - Question 1873 Calculate Special Bonus

### Attempt 1: Use apply()
```py
import pandas as pd

def calculate_special_bonus(employees: pd.DataFrame) -> pd.DataFrame:
    employees['bonus'] = employees.apply(lambda row: row['salary'] if row['employee_id'] % 2 == 1 and row['name'][0] != 'M' else 0, axis=1)
    return employees.sort_values('employee_id')[['employee_id', 'bonus']]
```
- Runtime: 422 ms (Beats: 99.22%)
- Memory: 66.78 MB (Beats: 33.60%)

<br>
