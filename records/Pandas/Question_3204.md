# [LeetCode Records](../../README.md) - Question 3204 Bitwise User Permissions Analysis

### Attempt 1: Use two for loops with & and | bitwise operators
```py
import pandas as pd

def analyze_permissions(user_permissions: pd.DataFrame) -> pd.DataFrame:
    common_perms = user_permissions['permissions'][0]
    for permission in user_permissions['permissions']:
        common_perms &= permission

    any_perms = user_permissions['permissions'][0]
    for permission in user_permissions['permissions']:
        any_perms |= permission

    return pd.DataFrame({
        'common_perms': [common_perms],
        'any_perms': [any_perms],
    })
```
- Runtime: 302 ms (Beats: 100.00%)
- Memory: 68.45 MB (Beats: 15.09%)

<br>
