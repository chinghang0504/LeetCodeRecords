# [LeetCode Records](../../README.md) - Question 2854 Rolling Average Steps

### Attempt 1: Use groupby(), apply(), shift() and np.round()
```py
import pandas as pd

def getAverage(df):
    sorted_df = df.sort_values('steps_date')
    sorted_df[['second_count', 'second_date']] = sorted_df[['steps_count', 'steps_date']].shift(1)
    sorted_df[['third_count', 'third_date']] = sorted_df[['steps_count', 'steps_date']].shift(2)
    sorted_df = sorted_df[(sorted_df['steps_date'] - sorted_df['second_date'] == np.timedelta64(1,'D')) & (sorted_df['steps_date'] - sorted_df['third_date'] == np.timedelta64(2,'D'))] 
    sorted_df['rolling_average'] = np.round((sorted_df['steps_count'] + sorted_df['second_count'] + sorted_df['third_count']) / 3, 2)
    return sorted_df

def rolling_average(steps: pd.DataFrame) -> pd.DataFrame:
    return steps.groupby('user_id').apply(getAverage)[['user_id', 'steps_date', 'rolling_average']]
```
- Runtime: 521 ms (Beats: 9.68%)
- Memory: 70.79 MB (Beats: 58.06%)

<br>
