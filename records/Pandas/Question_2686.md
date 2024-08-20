# [LeetCode Records](../../README.md) - Question 2686 Immediate Food Delivery III

### Attempt 1: Use astype(), groupby(), mean(), and np.round()
```py
import pandas as pd

def immediate_delivery(delivery: pd.DataFrame) -> pd.DataFrame:
    delivery['immediate_percentage'] = (delivery['order_date'] == delivery['customer_pref_delivery_date']).astype(np.float64)

    ans = delivery.groupby('order_date')['immediate_percentage'].mean().reset_index()
    ans['immediate_percentage'] = np.round(ans['immediate_percentage'] * 100, 2)
    
    return ans.sort_values('order_date')
```
- Runtime: 410 ms (Beats: 93.62%)
- Memory: 70.71 MB (Beats: 44.68%)

<br>
