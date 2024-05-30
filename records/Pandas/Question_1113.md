
# [LeetCode Records](../../README.md) - Question 1113 Reported Posts

### Attempt 1: Use groupby() and nunique()
```py
import pandas as pd

def reported_posts(actions: pd.DataFrame) -> pd.DataFrame:
    yesterday_actions_df = actions[(actions['action'] == 'report') & (actions['action_date'] == np.datetime64('2019-07-04'))]
    return yesterday_actions_df.groupby('extra')['post_id'].nunique().reset_index().rename(columns={'extra': 'report_reason', 'post_id': 'report_count'})
```
- Runtime: 540 ms (Beats: 98.08%)
- Memory: 67.96 MB (Beats: 71.15%)

<br>
