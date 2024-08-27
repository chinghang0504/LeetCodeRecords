# [LeetCode Records](../../README.md) - Question 1321 Restaurant Growth

### Attempt 1: Use groupby(), sum(), min(), np.timedelta64(), apply(), and np.round()
```py
import pandas as pd

def get_average(row, df):
    start_day = row['visited_on'] - np.timedelta64(6, 'D')
    end_day = row['visited_on']
    df = df[(df['visited_on'] >= start_day) & (df['visited_on'] <= end_day)]
    
    total_amount = df['amount'].sum()
    
    row['amount'] = total_amount
    row['average_amount'] = total_amount / 7

    return row


def restaurant_growth(customer: pd.DataFrame) -> pd.DataFrame:
    all_days = customer.groupby('visited_on')['amount'].sum().reset_index()
    start_day = all_days['visited_on'].min() + np.timedelta64(6, 'D')
    selected_days = all_days[all_days['visited_on'] >= start_day]

    ans = selected_days.apply(lambda row: get_average(row, all_days), axis=1)
    ans['average_amount'] = np.round(ans['average_amount'], 2)
    return ans[['visited_on', 'amount', 'average_amount']]
```
- Runtime: 458 ms (Beats: 31.17%)
- Memory: 70.54 MB (Beats: 68.83%)

<br>
