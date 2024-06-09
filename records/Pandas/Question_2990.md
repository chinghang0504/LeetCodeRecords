# [LeetCode Records](../../README.md) - Question 2990 Loan Types

### Attempt 1: Use isin() and to_frame()
```py
import pandas as pd

def loan_types(loans: pd.DataFrame) -> pd.DataFrame:
    refinance_user_id_sr = loans[loans['loan_type'] == 'Refinance']['user_id']
    mortgage_user_id_sr = loans[loans['loan_type'] == 'Mortgage']['user_id']
    return refinance_user_id_sr[refinance_user_id_sr.isin(mortgage_user_id_sr)].drop_duplicates().to_frame().sort_values('user_id')
```
- Runtime: 469 ms (Beats: 96.97%)
- Memory: 65.94 MB (Beats: 84.85%)

<br>
