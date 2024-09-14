# [LeetCode Records](../../README.md) - Question 3236 CEO Subordinate Hierarchy

### Attempt 1: Use dictionary to store the relationships
```py
import pandas as pd

def generate_relationships(relationships, row):
    relationships[row['employee_id']] = row['manager_id']


def get_hierarchy_level(relationships, row, manager_id):
    level = 1
    if not row['employee_id'] in relationships:
        return None
    curr_manager_id = relationships[row['employee_id']]
    
    while curr_manager_id != manager_id:
        if not curr_manager_id in relationships:
            return None
        curr_manager_id = relationships[curr_manager_id]
        level += 1
    return level


def find_subordinates(employees: pd.DataFrame) -> pd.DataFrame:
    manager = employees[employees['manager_id'].isna()].loc[0]
    manager_id = manager['employee_id']
    manager_salary = manager['salary']

    relationships = {}
    non_manager_employees = employees[~employees['manager_id'].isna()]
    non_manager_employees.apply(lambda row: generate_relationships(relationships, row), axis=1)
    non_manager_employees['hierarchy_level'] = non_manager_employees.apply(lambda row: get_hierarchy_level(relationships, row, manager_id), axis=1)
    non_manager_employees = non_manager_employees[~non_manager_employees['hierarchy_level'].isna()]
    non_manager_employees['salary_difference'] = non_manager_employees['salary'] - manager_salary

    ans = non_manager_employees.rename(columns={'employee_id': 'subordinate_id', 'employee_name': 'subordinate_name'})
    ans = ans.sort_values(['hierarchy_level', 'subordinate_id'])
    return ans[['subordinate_id', 'subordinate_name', 'hierarchy_level', 'salary_difference']]
```
- Runtime: 332 ms (Beats: 100.00%)
- Memory: 70.70 MB (Beats: 22.73%)

<br>
