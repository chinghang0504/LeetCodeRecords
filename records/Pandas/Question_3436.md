# [LeetCode Records](../../README.md) - Question 3436 Find Valid Emails

### Attempt 1: Use apply() to check every email
```py
import pandas as pd

def is_valid_email(email):
    email_splits = email.split('@')
    if len(email_splits) != 2:
        return False

    for ch in email_splits[0]:
        if ch >= 'a' and ch <= 'z':
            continue
        elif ch >= 'A' and ch <= 'Z':
            continue
        elif ch >= '0' and ch <= '9':
            continue
        elif ch == '_':
            continue
        else:
            return False

    if len(email_splits[1]) < 5:
        return False
    elif email_splits[1][-4:] != '.com':
        return False

    first_ch = email_splits[1][0]
    if first_ch >= 'a' and first_ch <= 'z':
        return True
    elif first_ch >= 'A' and first_ch <= 'Z':
        return True

    return False
    

def find_valid_emails(users: pd.DataFrame) -> pd.DataFrame:
    users['is_valid'] = users['email'].apply(is_valid_email)
    ans = users[users['is_valid']]
    return ans[['user_id', 'email']].sort_values('user_id')
```
- Runtime: 506 ms (Beats: 100.00%)
- Memory: 66.80 MB (Beats: 100.00%)

<br>
