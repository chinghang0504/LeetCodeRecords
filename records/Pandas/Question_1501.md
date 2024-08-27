# [LeetCode Records](../../README.md) - Question 1501 Countries You Can Safely Invest In

### Attempt 1: Use pd.concat(), value_counts(), groupby(), sum(), pd.merge(), and apply()
```py
import pandas as pd

def find_safe_countries(person: pd.DataFrame, country: pd.DataFrame, calls: pd.DataFrame) -> pd.DataFrame:
    callers = calls[['caller_id', 'duration']].rename(columns={'caller_id': 'id'})
    callees = calls[['callee_id', 'duration']].rename(columns={'callee_id': 'id'})

    all_calls = pd.concat([callers, callees])
    all_calls['id'].value_counts().rename('count').reset_index()
    durations = all_calls.groupby('id')['duration'].sum().reset_index()
    counts = all_calls['id'].value_counts().rename('count').reset_index()
    all_calls = pd.merge(durations, counts, on='id')

    average_duration = all_calls['duration'].sum() / all_calls['count'].sum()

    person['country_code'] = person['phone_number'].apply(lambda phone_number: phone_number[0:3])
    merged_df = pd.merge(all_calls, person, on='id')
    merged_df = merged_df.groupby('country_code')[['duration', 'count']].sum().reset_index()
    merged_df['average_duration'] = merged_df['duration'] / merged_df['count']

    selected_countries = merged_df[merged_df['average_duration'] > average_duration]
    return pd.merge(country, selected_countries, on='country_code')[['name']].rename(columns={'name': 'country'})
```
- Runtime: 566 ms (Beats: 30.51%)
- Memory: 72.40 MB (Beats: 6.78%)

<br>
