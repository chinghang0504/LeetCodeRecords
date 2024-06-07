# [LeetCode Records](../../README.md) - Question 1511 Customer Order Frequency

### Attempt 1: Use merge(), groupby(), sum(), and isin()
```py
import pandas as pd

def customer_order_frequency(customers: pd.DataFrame, product: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    orders_with_amount_df = pd.merge(orders, product, on='product_id')
    orders_with_amount_df['amount'] = orders_with_amount_df['quantity'] * orders_with_amount_df['price']
    june_orders_df = orders_with_amount_df[(orders_with_amount_df['order_date'].dt.year == 2020) & (orders_with_amount_df['order_date'].dt.month == 6)]
    june_customers_df = june_orders_df.groupby('customer_id')['amount'].sum().reset_index()
    june_customers_df = june_customers_df[june_customers_df['amount'] >= 100]
    july_orders_df = orders_with_amount_df[(orders_with_amount_df['order_date'].dt.year == 2020) & (orders_with_amount_df['order_date'].dt.month == 7)]
    july_customers_df = july_orders_df.groupby('customer_id')['amount'].sum().reset_index()
    july_customers_df = july_customers_df[july_customers_df['amount'] >= 100]
    return customers[customers['customer_id'].isin(june_customers_df['customer_id']) & customers['customer_id'].isin(july_customers_df['customer_id'])][['customer_id', 'name']]
```
- Runtime: 462 ms (Beats: 100.00%)
- Memory: 68.20 MB (Beats: 49.12%)

<br>
