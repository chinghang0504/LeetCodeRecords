# [LeetCode Records](../../README.md) - Question 2504 Concatenate the Name and the Profession

### Attempt 1: Use apply()
```py
import pandas as pd

def concatenate_info(person: pd.DataFrame) -> pd.DataFrame:
    person['name'] = person.apply(lambda row: f"{row['name']}({row['profession'][0]})", axis=1)
    return person[['person_id', 'name']].sort_values('person_id', ascending=False)
```
- Runtime: 375 ms (Beats: 94.74%)
- Memory: 66.53 MB (Beats: 52.63%)

<br>
