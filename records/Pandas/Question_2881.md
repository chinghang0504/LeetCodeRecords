# [LeetCode Records](../../README.md) - Question 2881 Create a New Colum

### Attempt 1: 
```py
import pandas as pd

def createBonusColumn(employees: pd.DataFrame) -> pd.DataFrame:
    employees['bonus'] = employees['salary'] * 2
    return employees
```
- Runtime: 364 ms (Beats: 99.31%)
- Memory: 65.94 MB (Beats: 5.41%)

<br>
