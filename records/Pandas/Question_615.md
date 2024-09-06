# [LeetCode Records](../../README.md) - Question 615 Average Salary: Departments VS Company

### Attempt 1: Calculate the average salary for each month first
```py
import pandas as pd

def get_comparison(row):
    if row['amount'] > row['average_salary']:
        return 'higher'
    elif row['amount'] < row['average_salary']:
        return 'lower'
    else:
        return 'same'
        

def average_salary(salary: pd.DataFrame, employee: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(salary, employee, on='employee_id')
    merged_df['pay_month'] = merged_df['pay_date'].dt.strftime('%Y-%m')

    average_salary = merged_df.groupby(['pay_month'])['amount'].mean().rename('average_salary').reset_index()
    average_department_salary = merged_df.groupby(['pay_month', 'department_id'])['amount'].mean().reset_index()

    ans = pd.merge(average_department_salary, average_salary, on='pay_month')
    ans['comparison'] = ans.apply(get_comparison, axis=1)
    return ans[['pay_month', 'department_id', 'comparison']]
```
- Runtime: 358 ms (Beats: 89.61%)
- Memory: 70.60 MB (Beats: 96.10%)

<br>
