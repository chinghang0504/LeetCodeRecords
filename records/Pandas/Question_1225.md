# [LeetCode Records](../../README.md) - Question 1225 Report Contiguous Dates

### Attempt 1: Group the same consecutive states together
```py
import pandas as pd

def combine_same_state(df):
    return pd.Series({
        'period_state': df['period_state'].iloc[0],
        'start_date': df['start_date'].min(),
        'end_date': df['end_date'].max()
    })


def report_contiguous_dates(failed: pd.DataFrame, succeeded: pd.DataFrame) -> pd.DataFrame:
    failed_2019 = failed[failed['fail_date'].dt.year == 2019]
    failed_2019 = failed_2019.rename(columns={'fail_date': 'start_date'})
    failed_2019['end_date'] = failed_2019['start_date']
    failed_2019['period_state'] = 'failed'

    succeeded_2019 = succeeded[succeeded['success_date'].dt.year == 2019]
    succeeded_2019 = succeeded_2019.rename(columns={'success_date': 'start_date'})
    succeeded_2019['end_date'] = succeeded_2019['start_date']
    succeeded_2019['period_state'] = 'succeeded'

    states = pd.concat([failed_2019, succeeded_2019])
    states = states.sort_values('start_date')

    prev_state = ''
    prev_num = 0
    rank_list = []
    for index, row in states.iterrows():
        curr_state = row['period_state']
        if curr_state != prev_state:
            prev_state = curr_state
            prev_num += 1
        rank_list.append(prev_num)
    states['rank'] = rank_list

    ans = states.groupby('rank').apply(combine_same_state)
    return ans[['period_state', 'start_date', 'end_date']]
```
- Runtime: 1083 ms (Beats: 5.88%)
- Memory: 72.17 MB (Beats: 31.76%)

<br>
