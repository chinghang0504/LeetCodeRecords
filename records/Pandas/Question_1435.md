# [LeetCode Records](../../README.md) - Question 1435 Create a Session Bar Chart

### Attempt 1: Use apply(), value_counts(), merge(), and fillna()
```py
import pandas as pd

def getType(duration):
    durationInMinute = duration / 60
    if durationInMinute < 5:
        return '[0-5>'
    elif durationInMinute < 10:
        return '[5-10>'
    elif durationInMinute < 15:
        return '[10-15>'
    else:
        return '15 or more'

def create_bar_chart(sessions: pd.DataFrame) -> pd.DataFrame:
    sessions['bin'] = sessions['duration'].apply(getType)
    total_df = sessions['bin'].value_counts().reset_index().rename(columns={'total': 'bin', 'count': 'total'})
    bin_df = pd.DataFrame({
        'bin': ['[0-5>', '[5-10>', '[10-15>', '15 or more']
    })
    return pd.merge(bin_df, total_df, on='bin', how='left').fillna(0)
```
- Runtime: 558 ms (Beats: 92.59%)
- Memory: 67.26 MB (Beats: 5.55%)

<br>
