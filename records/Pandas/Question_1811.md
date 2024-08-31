# [LeetCode Records](../../README.md) - Question 1811 Find Interview Candidates

### Attempt 1: Use shift(), dropna(), pd.concat(), apply(), value_counts(), rename_axis(), drop_duplicates(), and isin()
```py
import pandas as pd

def get_medal_counts(row):
    medal_counts = row.value_counts().rename_axis('user_id').reset_index()
    medal_counts = medal_counts[medal_counts['count'] >= 3][['user_id']]
    return medal_counts


def find_interview_candidates(contests: pd.DataFrame, users: pd.DataFrame) -> pd.DataFrame:
    consecutive_contents = contests.rename(columns={'gold_medal': 'a', 'silver_medal': 'b', 'bronze_medal': 'c'})[['a', 'b', 'c']]
    consecutive_contents[['d', 'e', 'f']] = consecutive_contents[['a', 'b', 'c']].shift(-1)
    consecutive_contents[['g', 'h', 'i']] = consecutive_contents[['a', 'b', 'c']].shift(-2)
    consecutive_contents = consecutive_contents.dropna()
    condition_1_users = pd.concat([*consecutive_contents.apply(get_medal_counts, axis=1)])

    gold_medal_counts = contests['gold_medal'].value_counts().rename_axis('user_id').reset_index()
    condition_2_users = gold_medal_counts[gold_medal_counts['count'] >= 3][['user_id']]

    selected_users = pd.concat([condition_1_users, condition_2_users]).drop_duplicates()

    return users[users['user_id'].isin(selected_users['user_id'])][['name', 'mail']]
```
- Runtime: 5300 ms (Beats: 5.88%)
- Memory: 73.88 MB (Beats: 11.76%)

<br>
