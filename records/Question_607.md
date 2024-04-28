# [LeetCode Records](../README.md) - Question 607 Sales Person

### Attempt 1: 
```py
import pandas as pd

def sales_person(sales_person: pd.DataFrame, company: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    RED_com_id_list = company[company['name'] == 'RED']['com_id']

    if len(RED_com_id_list.index) == 0:
        return sales_person[['name']]
    else:
        RED_com_id = RED_com_id_list.iloc[0]
        RED_sales_id = orders[orders['com_id'] == RED_com_id]['sales_id']
        return sales_person[~sales_person['sales_id'].isin(RED_sales_id)][['name']]
```
- Runtime: 809 ms (Beats: 68.96%)
- Memory: 66.42 MB (Beats: 91.29%)

<br>
