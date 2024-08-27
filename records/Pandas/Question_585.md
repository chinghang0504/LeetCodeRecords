# [LeetCode Records](../../README.md) - Question 585 Investments in 2016

### Attempt 1: Use value_counts(), pd.merge(), isin(), and np.round()
```py
import pandas as pd

def find_investments(insurance: pd.DataFrame) -> pd.DataFrame:
    location_counts = insurance[['lat', 'lon']].value_counts().rename('count').reset_index()
    location_counts = location_counts[location_counts['count'] == 1]

    tiv_2015_counts = insurance['tiv_2015'].value_counts().rename('count').reset_index().rename(columns={'index': 'tiv_2015'})
    tiv_2015_counts = tiv_2015_counts[tiv_2015_counts['count'] >= 2]

    merged_df = pd.merge(insurance, location_counts, on=['lat', 'lon'])
    merged_df = merged_df[merged_df['tiv_2015'].isin(tiv_2015_counts['tiv_2015'])]

    return pd.DataFrame({
        'tiv_2016': np.round([merged_df['tiv_2016'].sum()], 2)
    })
```
- Runtime: 420 ms (Beats: 75.37%)
- Memory: 71.36 MB (Beats: 15.73%)

<br>
