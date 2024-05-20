# [LeetCode Records](../../README.md) - Question 1098 Unpopular Books

### Attempt 1: Use groupby(), sum(), and isin()
```py
import pandas as pd

def unpopular_books(books: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    last_year_orders = orders[(orders['dispatch_date'] >= np.datetime64('2018-06-23')) & (orders['dispatch_date'] < np.datetime64('2019-06-23'))]
    last_year_counts = last_year_orders.groupby('book_id')['quantity'].sum().reset_index()
    more_than_9_book_id = last_year_counts[last_year_counts['quantity'] >= 10]['book_id']
    less_than_1_month_book_id = books[(books['available_from'] >= np.datetime64('2019-05-23')) & (books['available_from'] <= np.datetime64('2019-06-23'))]['book_id']
    return books[(~books['book_id'].isin(more_than_9_book_id)) & (~books['book_id'].isin(less_than_1_month_book_id))][['book_id', 'name']]
```
- Runtime: 612 ms (Beats: 92.86%)
- Memory: 68.37 MB (Beats: 83.33%)

<br>
