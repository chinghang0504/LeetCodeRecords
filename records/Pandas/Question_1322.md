# [LeetCode Records](../../README.md) - Question 1322 Ads Performance

### Attempt 1: Use groupby(), count(), pd.merge(), isin(), and pd.concat()
```py
import pandas as pd

def ads_performance(ads: pd.DataFrame) -> pd.DataFrame:
    clicked_action_df = ads[ads['action'] == 'Clicked'].groupby('ad_id')['user_id'].count().rename('clicked').reset_index()
    viewed_action_df = ads[ads['action'] == 'Viewed'].groupby('ad_id')['user_id'].count().rename('viewed').reset_index()
    merged_df = pd.merge(clicked_action_df, viewed_action_df, on='ad_id', how='outer').fillna(0)
    merged_df['ctr'] = round(merged_df['clicked'] / (merged_df['clicked'] + merged_df['viewed']) * 100, 2)
    merged_df = merged_df[['ad_id', 'ctr']]

    zero_view_id = ads[~ads['ad_id'].isin(merged_df['ad_id'])]['ad_id']
    zero_view_ad = pd.DataFrame({
        'ad_id': zero_view_id,
        'ctr': np.zeros(zero_view_id.size)
    })

    return pd.concat([zero_view_ad, merged_df]).sort_values(['ctr', 'ad_id'], ascending=[False, True]).drop_duplicates()
```
- Runtime: 452 ms (Beats: 91.39%)
- Memory: 71.37 MB (Beats: 19.49%)

<br>
