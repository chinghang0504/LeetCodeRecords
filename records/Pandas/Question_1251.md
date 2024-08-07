# [LeetCode Records](../../README.md) - Question 1251 Average Selling Price

### Attempt 1: Use pd.merge(), groupby(), sum(), apply(), isin(), and pd.concat()
```py
import pandas as pd

def average_selling_price(prices: pd.DataFrame, units_sold: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(units_sold, prices, on='product_id')
    merged_df = merged_df[(merged_df['start_date'] <= merged_df['purchase_date']) & (merged_df['purchase_date'] <= merged_df['end_date'])]
    merged_df['total_price'] = merged_df['units'] * merged_df['price']

    average_df = merged_df.groupby('product_id')[['units', 'total_price']].sum().reset_index()
    average_df['average_price'] = average_df['total_price'] / average_df['units']
    average_df['average_price'] = average_df['average_price'].apply(lambda x: int(x * 100 + 0.5) / 100)
    average_df = average_df[['product_id', 'average_price']]

    zero_sold_product_id = prices[~prices['product_id'].isin(average_df['product_id'])][['product_id']]
    return pd.concat([average_df, zero_sold_product_id]).fillna(0)
```
- Runtime: 448 ms (Beats: 92.07%)
- Memory: 71.44 MB (Beats: 8.65%)

<br>
