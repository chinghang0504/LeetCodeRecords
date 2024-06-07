# [LeetCode Records](../../README.md) - Question 1667 Fix Names in a Table

### Attempt 1: Use apply()
```py
import pandas as pd

def fixName(name):
    name = name[0].upper() + name[1:].lower()
    return name

def fix_names(users: pd.DataFrame) -> pd.DataFrame:
    users['name'] = users['name'].apply(fixName)
    return users.sort_values('user_id')
```
- Runtime: 403 ms (Beats: 99.62%)
- Memory: 67.21 MB (Beats: 7.35%)

<br>
