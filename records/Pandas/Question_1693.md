# [LeetCode Records](../../README.md) - Question 1693 Daily Leads and Partners

### Attempt 1: Use groupby() and nunique()
```py
import pandas as pd

def daily_leads_and_partners(daily_sales: pd.DataFrame) -> pd.DataFrame:
    return daily_sales.groupby(['date_id', 'make_name'])[['lead_id', 'partner_id']].nunique().rename(columns={'lead_id': 'unique_leads', 'partner_id': 'unique_partners'}).reset_index()
```
- Runtime: 437 ms (Beats: 99.42%)
- Memory: 67.44 MB (Beats: 34.10%)

<br>
