# [LeetCode Records](../../README.md) - Question 1821 Find Customers With Positive Revenue this Year

### Attempt 1: 
```py
import pandas as pd

def find_customers(customers: pd.DataFrame) -> pd.DataFrame:
    return customers[(customers['year'] == 2021) & (customers['revenue'] > 0)][['customer_id']]
```
- Runtime: 425 ms (Beats: 100.00%)
- Memory: 66.10 MB (Beats: 35.13%)

<br>
