# [LeetCode Records](../../README.md) - Question 1468 Calculate Salaries

### Attempt 1: Use groupby(), max(), apply(), and pd.merge()
```py
import pandas as pd

def calculateTaxRate(salary):
    if salary < 1000:
        return 0.0
    elif salary <= 10000:
        return 0.24
    else:
        return 0.49

def calculate_salaries(salaries: pd.DataFrame) -> pd.DataFrame:
    max_salaries = salaries.groupby('company_id')['salary'].max().reset_index()
    max_salaries['rate'] = max_salaries['salary'].apply(calculateTaxRate)
    max_salaries = max_salaries[['company_id', 'rate']]

    ans = pd.merge(salaries, max_salaries, on='company_id')
    ans['salary'] = ans['salary'] * (1 - ans['rate'])
    ans['salary'] = ans['salary'].apply(lambda x: int(x + 0.5))

    return ans[['company_id','employee_id','employee_name','salary']]
```
- Runtime: 403 ms (Beats: 90.70%)
- Memory: 71.82 MB (Beats: 6.98%)

<br>
