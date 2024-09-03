# [LeetCode Records](../../README.md) - Question 1767 Find the Subtasks That Did Not Execute

### Attempt 1: Use a function that generates all the subtask ids
```py
import pandas as pd

def get_all_rows(row):
    task_id = row['task_id']
    subtasks_count = row['subtasks_count']
    return pd.DataFrame({
        'task_id': np.repeat(task_id, subtasks_count),
        'subtask_id': np.arange(1, subtasks_count + 1),
    })


def find_subtasks(tasks: pd.DataFrame, executed: pd.DataFrame) -> pd.DataFrame:
    all_rows = pd.concat([*tasks.apply(get_all_rows, axis=1)])
    executed['is_executed'] = True

    ans = pd.merge(all_rows, executed, on=['task_id', 'subtask_id'], how='left')
    ans = ans[ans['is_executed'].isna()]
    return ans[['task_id', 'subtask_id']]
```
- Runtime: 417 ms (Beats: 73.81%)
- Memory: 71.08 MB (Beats: 21.43%)

<br>
