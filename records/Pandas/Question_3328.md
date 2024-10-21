# [LeetCode Records](../../README.md) - Question 3328 Find Cities in Each State II

### Attempt 1: Find the valid states first
```py
import pandas as pd

def state_city_analysis(cities: pd.DataFrame) -> pd.DataFrame:
    num_of_cities = cities.groupby('state')['city'].nunique().reset_index()
    at_least_three_cities_states = num_of_cities[num_of_cities['city'] >= 3][['state']]

    cities['same_start_letter'] = cities.apply(lambda row: row['city'].startswith(row['state'][0]), axis=1)
    same_start_letter_cities = cities[cities['same_start_letter']][['state']].drop_duplicates()
    matching_letter_counts = cities[cities['same_start_letter']].groupby('state')['city'].nunique().rename('matching_letter_count').reset_index()

    valid_states = pd.merge(at_least_three_cities_states, same_start_letter_cities, on='state')['state']
    selected_cities = cities[cities['state'].isin(valid_states)]
    selected_cities = selected_cities.sort_values(['state', 'city'])

    if len(selected_cities.index) == 0:
        return pd.DataFrame({
            'state': [],
            'cities': [],
            'matching_letter_count': [],
        })
    else:
        selected_cities = selected_cities.groupby('state').apply(lambda row: ', '.join(row['city'])).rename('cities').reset_index()

    ans = pd.merge(selected_cities, matching_letter_counts, on='state')
    ans = ans.sort_values(['matching_letter_count', 'state'], ascending=[False, True])

    return ans
```
- Runtime: 424 ms (Beats: 100.00%)
- Memory: 71.06 MB (Beats: 100.00%)

<br>
