# [LeetCode Records](../../README.md) - Question 2480 Form a Chemical Bond

### Attempt 1: Use merge()
```py
import pandas as pd

def form_bond(elements: pd.DataFrame) -> pd.DataFrame:
    metal_df = elements[elements['type'] == 'Metal'][['symbol']]
    non_metal_df = elements[elements['type'] == 'Nonmetal'][['symbol']]
    return pd.merge(metal_df, non_metal_df, how='cross').rename(columns={'symbol_x': 'metal', 'symbol_y': 'nonmetal'})
```
- Runtime: 584 ms (Beats: 100.00%)
- Memory: 99.71 MB (Beats: 76.47%)

<br>
