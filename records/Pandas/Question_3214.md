# [LeetCode Records](../../README.md) - Question 3214 Year on Year Growth Rate

### Attempt 1: Calculate the total spend for each year first
```py
import pandas as pd

def calculate_yoy_growth(user_transactions: pd.DataFrame) -> pd.DataFrame:
    user_transactions['transaction_date'] = pd.to_datetime(user_transactions['transaction_date'])
    user_transactions['year'] = user_transactions['transaction_date'].dt.year

    ans = user_transactions.groupby(['product_id', 'year'])['spend'].sum().rename('curr_year_spend').reset_index()
    ans['prev_year_spend'] = ans.groupby('product_id')['curr_year_spend'].shift(1)
    ans['yoy_rate'] = np.round((ans['curr_year_spend'] - ans['prev_year_spend']) / ans['prev_year_spend'] * 100, 2)
    return ans[['year', 'product_id', 'curr_year_spend', 'prev_year_spend', 'yoy_rate']]
```
- Runtime: 342 ms (Beats: 97.78%)
- Memory: 70.90 MB (Beats: 57.78%)

<br>
