# [LeetCode Records](../../README.md) - Question 196 Delete Duplicate Emails

### Attempt 1: Get the index of email and then drop others
```py
import pandas as pd

def delete_duplicate_emails(person: pd.DataFrame) -> None:
    min_id = person.groupby('email')['id'].idxmin()
    person.drop(person.index.difference(min_id), inplace=True)
```
- Runtime: 628 ms (Beats: 44.81%)
- Memory: 65.75 MB (Beats: 81.09%)

<br>

### Attempt 2: Sort first and then drop duplicates
```py
import pandas as pd

def delete_duplicate_emails(person: pd.DataFrame) -> None:
    person.sort_values('id', inplace=True)
    person.drop_duplicates('email', inplace=True)
```
- Runtime: 535 ms (Beats: 82.43%)
- Memory: 66.60 MB (Beats: 18.05%)

<br>
