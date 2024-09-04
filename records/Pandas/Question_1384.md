# [LeetCode Records](../../README.md) - Question 1384 Total Sales Amount by Year

### Attempt 1: Use apply() to get a data frame of the report year and the total amount
```py
import pandas as pd

def get_total_amounts(row):
    start_year = row['period_start'].year
    end_year = row['period_end'].year
    total_amounts = []
    
    if start_year == end_year:
        num_of_days = (row['period_end'] - row['period_start']) / np.timedelta64(1, 'D') + 1
        total_amounts.append(num_of_days * row['average_daily_sales'])
    else:
        num_of_days = (np.datetime64(f'{start_year}-12-31') - row['period_start']) / np.timedelta64(1, 'D') + 1
        total_amounts.append(num_of_days * row['average_daily_sales'])
        
        year = start_year + 1
        while year < end_year:
            num_of_days = (np.datetime64(f'{year}-12-31') - np.datetime64(f'{year}-01-01')) / np.timedelta64(1, 'D') + 1
            total_amounts.append(num_of_days * row['average_daily_sales'])
            year = year + 1
            
        num_of_days = (row['period_end'] - np.datetime64(f'{year}-01-01')) / np.timedelta64(1, 'D') + 1
        total_amounts.append(num_of_days * row['average_daily_sales'])
        
    return pd.DataFrame({
        'product_id': np.full(len(total_amounts), row['product_id']),
        'report_year': np.arange(start_year, end_year + 1),
        'total_amount': total_amounts
    })


def total_sales(product: pd.DataFrame, sales: pd.DataFrame) -> pd.DataFrame:
    total_amounts = pd.concat([*sales.apply(get_total_amounts, axis=1)])
    total_amounts['report_year'] = total_amounts['report_year'].apply(lambda year: str(year))
    
    ans = pd.merge(total_amounts, product, on='product_id')
    return ans.sort_values(['product_id', 'report_year'])[['product_id', 'product_name', 'report_year', 'total_amount']]
```
- Runtime: 346 ms (Beats: 100.00%)
- Memory: 71.15 MB (Beats: 73.33%)

<br>
