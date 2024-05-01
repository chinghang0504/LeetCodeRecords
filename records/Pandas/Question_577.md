# [LeetCode Records](../../README.md) - Question 577 Employee Bonus

### Attempt 1: Use left join
```py
import pandas as pd

def employee_bonus(employee: pd.DataFrame, bonus: pd.DataFrame) -> pd.DataFrame:
    rejectedBonus = bonus[bonus['bonus'] >= 1000]
    selectedEmployee = employee[~employee['empId'].isin(rejectedBonus['empId'])]
    return pd.merge(selectedEmployee, bonus, on=['empId'], how='left')[['name', 'bonus']]
```
- Runtime: 622 ms (Beats: 91.30%)
- Memory: 66.92 MB (Beats: 70.61%)

<br>
