# [LeetCode Records](../README.md) - Question 182 Duplicate Emails

### Attempt 1: Use count()
```py
import pandas as pd

def duplicate_emails(person: pd.DataFrame) -> pd.DataFrame:
    email_counts = person.groupby('email').count().reset_index()
    email_counts = email_counts[email_counts['id'] >= 2]
    return pd.DataFrame({'Email': email_counts['email']})
```
- Runtime: 677 ms (Beats: 29.16%)
- Memory: 66.28 MB (Beats: 24.70%)

<br>
