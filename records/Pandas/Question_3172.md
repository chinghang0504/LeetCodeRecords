# [LeetCode Records](../../README.md) - Question 3172 Second Day Verification

### Attempt 1: Use merge(), dt.floor(), and np.timedelta64()
```py
import pandas as pd

def find_second_day_signups(emails: pd.DataFrame, texts: pd.DataFrame) -> pd.DataFrame:
    verified_email_df = texts[texts['signup_action'] == 'Verified']
    merged_df = pd.merge(emails, verified_email_df, on='email_id')
    merged_df['next_date'] = merged_df['signup_date'].dt.floor('d') + np.timedelta64(1, 'D')
    second_day_df = merged_df[merged_df['action_date'].dt.floor('d') == merged_df['next_date']]
    return second_day_df[['user_id']].sort_values('user_id')
```
- Runtime: 417 ms (Beats: 100.00%)
- Memory: 68.06 MB (Beats: 18.18%)

<br>
