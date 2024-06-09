# [LeetCode Records](../../README.md) - Question 3059 Find All Unique Email Domains

### Attempt 1: Use apply() and size()
```py
import pandas as pd

def getEmailDomain(email):
    email_domain = email.rsplit('@')[-1]
    if email_domain[-4:] == '.com':
        return email_domain
    else:
        return None

def find_unique_email_domains(emails: pd.DataFrame) -> pd.DataFrame:
    emails['email_domain'] = emails['email'].apply(getEmailDomain)
    return emails.groupby('email_domain').size().rename('count').reset_index().sort_values('email_domain')
```
- Runtime: 370 ms (Beats: 100.00%)
- Memory: 66.02 MB (Beats: 62.50%)

<br>
