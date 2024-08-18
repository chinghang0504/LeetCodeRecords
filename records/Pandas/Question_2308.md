# [LeetCode Records](../../README.md) - Question 2308 Arrange Table by Gender

### Attempt 1: Use len(), max(), and append()
```py
import pandas as pd

def arrange_table(genders: pd.DataFrame) -> pd.DataFrame:
    female_genders = genders[genders['gender'] == 'female'].sort_values('user_id')
    other_genders = genders[genders['gender'] == 'other'].sort_values('user_id')
    male_genders = genders[genders['gender'] == 'male'].sort_values('user_id')

    female_len = len(female_genders)
    other_len = len(other_genders)
    male_len = len(male_genders)

    id_list = []
    gender_list = []

    max_len = max(max(female_len, other_len), male_len)
    i = 0
    while i < max_len:
        if i < female_len:
            id_list.append(female_genders.iloc[i]['user_id'])
            gender_list.append(female_genders.iloc[i]['gender'])
        if i < other_len:
            id_list.append(other_genders.iloc[i]['user_id'])
            gender_list.append(other_genders.iloc[i]['gender'])
        if i < male_len:
            id_list.append(male_genders.iloc[i]['user_id'])
            gender_list.append(male_genders.iloc[i]['gender'])
        i += 1

    return pd.DataFrame({
        'user_id': id_list,
        'gender': gender_list
    })
```
- Runtime: 606 ms (Beats: 8.70%)
- Memory: 70.26 MB (Beats: 43.48%)

<br>
