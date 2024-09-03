# [LeetCode Records](../../README.md) - Question 2793 Status of Flight Tickets

### Attempt 1: Use rank() to rank the passengers according to their booking time
```py
import pandas as pd

def ticket_status(flights: pd.DataFrame, passengers: pd.DataFrame) -> pd.DataFrame:
    merged_df = pd.merge(passengers, flights, on='flight_id')
    merged_df['rank'] = merged_df.groupby('flight_id')['booking_time'].rank()
    merged_df['Status'] = merged_df.apply(lambda row: 'Confirmed' if row['rank'] <= row['capacity'] else 'Waitlist', axis=1)
    return merged_df.sort_values('passenger_id')[['passenger_id', 'Status']]
```
- Runtime: 368 ms (Beats: 79.17%)
- Memory: 71.15 MB (Beats: 83.33%)

<br>
