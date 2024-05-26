# [LeetCode Records](../../README.md) - Question 1294 Weather Type in Each Country

### Attempt 1: Use apply()
```py
import pandas as pd

def get_weather_type(average_weather_state):
    if average_weather_state <= 15:
        return 'Cold'
    elif average_weather_state >= 25:
        return 'Hot'
    else:
        return 'Warm'

def weather_type(countries: pd.DataFrame, weather: pd.DataFrame) -> pd.DataFrame:
    selected_weather = weather[(weather['day'] >= np.datetime64('2019-11-01')) & (weather['day'] <= np.datetime64('2019-11-30'))]
    mean_df = selected_weather.groupby('country_id')['weather_state'].mean().reset_index()
    merged_df = pd.merge(countries, mean_df, on='country_id')
    merged_df['weather_type'] = merged_df['weather_state'].apply(get_weather_type)
    return merged_df[['country_name', 'weather_type']]
```
- Runtime: 554 ms (Beats: 100.00%)
- Memory: 68.02 MB (Beats: 54.65%)

<br>
