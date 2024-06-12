# [LeetCode Records](../../README.md) - Question 2372 Calculate the Influence of Each Salesperson

### Attempt 1: Use merge(), groupby(), sum(), and fillna()
```py
import pandas as pd

def calculate_influence(salesperson: pd.DataFrame, customer: pd.DataFrame, sales: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(customer, sales, on='customer_id').groupby('salesperson_id')['price'].sum().rename('total').reset_index()
    return pd.merge(salesperson, merged_df, on='salesperson_id', how='outer').fillna(0)
```
- Runtime: 474 ms (Beats: 100.00%)
- Memory: 66.93 MB (Beats: 86.36%)

<br>
