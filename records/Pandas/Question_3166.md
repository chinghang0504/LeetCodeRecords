# [LeetCode Records](../../README.md) - Question 3166 Calculate Parking Fees and Duration

### Attempt 1: Use dt.total_seconds(), groupby(), agg(), np.round(), sum(), loc[], idxmax(), and pd.merge()
```py
import pandas as pd

def calculate_fees_and_duration(parking_transactions: pd.DataFrame) -> pd.DataFrame:
    parking_transactions['diff_time_in_seconds'] = (parking_transactions['exit_time'] - parking_transactions['entry_time']).dt.total_seconds()

    total = parking_transactions.groupby('car_id').agg({'fee_paid': 'sum', 'diff_time_in_seconds': 'sum'})
    total['avg_hourly_fee'] = np.round(total['fee_paid'] / (total['diff_time_in_seconds'] / 3600), 2)

    total_time = parking_transactions.groupby(['car_id', 'lot_id'])['diff_time_in_seconds'].sum().rename('sum').reset_index()
    total_time = total_time.loc[total_time.groupby('car_id')['sum'].idxmax()]

    ans = pd.merge(total, total_time, on='car_id').rename(columns={'fee_paid': 'total_fee_paid', 'lot_id': 'most_time_lot'})
    return ans[['car_id', 'total_fee_paid', 'avg_hourly_fee', 'most_time_lot']]
```
- Runtime: 422 ms (Beats: 93.48%)
- Memory: 71.20 MB (Beats: 78.26%)

<br>
