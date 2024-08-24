# [LeetCode Records](../../README.md) - Question 1907 Count Salary Categories

### Attempt 1: Use apply(), value_counts(), rename_axis(), rename(), pd.merge(), and fillna()
```py
import pandas as pd

def get_salary_category(income):
    if income < 20000:
        return 'Low Salary'
    elif income <= 50000:
        return 'Average Salary'
    else:
        return 'High Salary'


def count_salary_categories(accounts: pd.DataFrame) -> pd.DataFrame:
    accounts['category'] = accounts['income'].apply(get_salary_category)

    counts = accounts['category'].value_counts().rename_axis('category').rename('accounts_count').reset_index()

    categories = pd.DataFrame({
        'category': ['Low Salary', 'Average Salary', 'High Salary']
    })
    return pd.merge(counts, categories, on='category', how='right').fillna(0)
```
- Runtime: 433 ms (Beats: 73.21%)
- Memory: 95.94 MB (Beats: 11.91%)

<br>
