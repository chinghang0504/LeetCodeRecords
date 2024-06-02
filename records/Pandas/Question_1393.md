# [LeetCode Records](../../README.md) - Question 1393 Capital Gain/Loss

### Attempt 1: Use apply(), groupby(), and sum()
```py
import pandas as pd

def capital_gainloss(stocks: pd.DataFrame) -> pd.DataFrame:
    stocks['factor'] = stocks.apply(lambda row: -1 if row['operation'] == 'Buy' else 1, axis=1)
    stocks['capital_gain_loss'] = stocks['price'] * stocks['factor']
    return stocks.groupby('stock_name')['capital_gain_loss'].sum().reset_index()
```
- Runtime: 513 ms (Beats: 100.00%)
- Memory: 66.74 MB (Beats: 75.00%)

<br>
