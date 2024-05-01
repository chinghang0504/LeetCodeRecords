# [LeetCode Records](../../README.md) - Question 197 Rising Temperature

### Attempt 1: Use shift() twice
```py
import pandas as pd

def rising_temperature(weather: pd.DataFrame) -> pd.DataFrame:
    weather = weather.sort_values('recordDate')
    weather['prev_temperature'] = weather['temperature'].shift(1)
    weather['prev_recordDate'] = weather['recordDate'].shift(1)
    weather['prev_recordDate'] = weather['prev_recordDate'].apply(lambda x: x + np.timedelta64(1, 'D'))
    result = weather[(weather['temperature'] > weather['prev_temperature']) & (weather['recordDate'] == weather['prev_recordDate'])]
    return pd.DataFrame({'id': result['id']})
```
- Runtime: 756 ms (Beats: 24.45%)
- Memory: 67.70 MB (Beats: 32.65%)

<br>
