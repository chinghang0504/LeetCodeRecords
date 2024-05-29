# [LeetCode Records](../../README.md) - Question 1270 All People Report to the Given Manager

### Attempt 1: Use isin() and concat()
```py
import pandas as pd

def find_reporting_people(employees: pd.DataFrame) -> pd.DataFrame:
    first_level_managers = employees[(employees['manager_id'] == 1) & (employees['employee_id'] != 1)]['employee_id']
    second_level_managers = employees[employees['manager_id'].isin(first_level_managers)]['employee_id']
    third_level_managers = employees[employees['manager_id'].isin(second_level_managers)]['employee_id']
    return pd.concat([first_level_managers, second_level_managers, third_level_managers], axis=0).reset_index()[['employee_id']]
```
- Runtime: 551 ms (Beats: 90.32%)
- Memory: 65.39 MB (Beats: 93.55%)

<br>
