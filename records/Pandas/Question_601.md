# [LeetCode Records](../../README.md) - Question 601 Human Traffic of Stadium

### Attempt 1: Use shift() to get the consecutive id's
```py
import pandas as pd

def human_traffic(stadium: pd.DataFrame) -> pd.DataFrame:
    people = stadium[stadium['people'] >= 100]
    people['second_id'] = people['id'].shift(-1)
    people['third_id'] = people['id'].shift(-2)
    selected_people = people[(people['id'] + 1 == people['second_id']) & (people['id'] + 2 == people['third_id'])]

    first_id = selected_people[['id']]
    second_id = selected_people[['second_id']].rename(columns={'second_id': 'id'})
    third_id = selected_people[['third_id']].rename(columns={'third_id': 'id'})
    selected_id = pd.concat([first_id, second_id, third_id]).drop_duplicates()

    return pd.merge(stadium, selected_id, on='id').sort_values('visit_date')
```
- Runtime: 389 ms (Beats: 68.15%)
- Memory: 70.78 MB (Beats: 18.27%)

<br>
