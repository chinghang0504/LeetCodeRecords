# [LeetCode Records](../../README.md) - Question 2346 Compute the Rank as a Percentage

### Attempt 1: Use groupby(), rank(), value_counts(), pd.merge(), apply(), and np.round()
```py
import pandas as pd

def compute_rating(students: pd.DataFrame) -> pd.DataFrame:
    students['rank'] = students.groupby('department_id')['mark'].rank(method='min', ascending=False).rename('rank')
    student_counts = students['department_id'].value_counts().reset_index()

    ans = pd.merge(students, student_counts, on='department_id')
    ans['percentage'] = ans.apply(lambda row: 0.0 if row['count'] == 1 else (row['rank'] - 1) * 100 / (row['count'] - 1), axis=1)
    ans['percentage'] = np.round(ans['percentage'], 2)
    return ans[['student_id', 'department_id', 'percentage']]
```
- Runtime: 617 ms (Beats: 25.00%)
- Memory: 71.92 MB (Beats: 18.75%)

<br>
