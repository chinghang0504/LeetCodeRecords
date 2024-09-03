# [LeetCode Records](../../README.md) - Question 2362 Generate the Invoice

### Attempt 1: Calculate the total of the invoices first
```py
import pandas as pd

def generate_the_invoice(products: pd.DataFrame, purchases: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(purchases, products, on='product_id', how='left')
    merged_df['price'] = merged_df['quantity'] * merged_df['price']

    invoice_totals = merged_df.groupby('invoice_id')['price'].sum().reset_index()
    min_invoice_id = invoice_totals[invoice_totals['price'] == invoice_totals['price'].max()]['invoice_id'].min()

    return merged_df[merged_df['invoice_id'] == min_invoice_id][['product_id', 'quantity', 'price']]
```
- Runtime: 370 ms (Beats: 100.00%)
- Memory: 71.72 MB (Beats: 63.33%)

<br>
