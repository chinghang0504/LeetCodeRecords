# [LeetCode Records](../../README.md) - Question 3050 Pizza Toppings Cost Analysis

### Attempt 1: Use pd.merge() and np.round()
```py
import pandas as pd

def cost_analysis(toppings: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(toppings, toppings, how='cross')
    merged_df = pd.merge(merged_df, toppings, how='cross')
    merged_df = merged_df[(merged_df['topping_name_x'] < merged_df['topping_name_y']) & (merged_df['topping_name_y'] < merged_df['topping_name'])]
    
    merged_df['total_cost'] = np.round(merged_df['cost_x'] + merged_df['cost_y'] + merged_df['cost'], decimals=2)
    merged_df['pizza'] = merged_df['topping_name_x'] + ',' + merged_df['topping_name_y'] + ',' + merged_df['topping_name']

    return merged_df[['pizza', 'total_cost']].sort_values(['total_cost', 'pizza'], ascending=[False, True])
```
- Runtime: 400 ms (Beats: 96.43%)
- Memory: 71.48 MB (Beats: 32.14%)

<br>
