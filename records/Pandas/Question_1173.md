# [LeetCode Records](../../README.md) - Question 1173 Immediate Food Delivery I

### Attempt 1: 
```py
import pandas as pd

def food_delivery(delivery: pd.DataFrame) -> pd.DataFrame:
    same_day_df = delivery[delivery['order_date'] == delivery['customer_pref_delivery_date']]
    return pd.DataFrame({
        'immediate_percentage': [round(len(same_day_df.index) / len(delivery.index) * 100, 2)]
    })
```
- Runtime: 527 ms (Beats: 97.46%)
- Memory: 66.63 MB (Beats: 60.84%)

<br>
