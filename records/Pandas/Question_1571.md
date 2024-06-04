# [LeetCode Records](../../README.md) - Question 1571 Warehouse Manager

### Attempt 1: Use merge(), groupby(), and sum()
```py
import pandas as pd

def warehouse_manager(warehouse: pd.DataFrame, products: pd.DataFrame) -> pd.DataFrame:
    products['unit_volume'] = products['Width'] * products['Length'] * products['Height']
    merged_df = pd.merge(warehouse, products, on='product_id')
    merged_df['volume'] = merged_df['units'] * merged_df['unit_volume']
    return merged_df.groupby('name')['volume'].sum().reset_index().rename(columns={'name': 'warehouse_name'})
```
- Runtime: 538 ms (Beats: 98.11%)
- Memory: 67.05 MB (Beats: 60.38%)

<br>
