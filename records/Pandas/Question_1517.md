# [LeetCode Records](../../README.md) - Question 1517 Find Users With Valid E-Mails

### Attempt 1: Use re.match(), and apply()
```py
import pandas as pd

def isValidEmail(email):
    email_pattern = r'^[a-zA-Z][a-zA-Z0-9\_\.\-]*@leetcode\.com$'
    return bool(re.match(email_pattern, email))


def valid_emails(users: pd.DataFrame) -> pd.DataFrame:
    users['is_valid'] = users['mail'].apply(lambda x: isValidEmail(x))
    return users[users['is_valid']][['user_id', 'name', 'mail']]
```
- Runtime: 352 ms (Beats: 94.79%)
- Memory: 69.99 MB (Beats: 32.89%)

<br>
