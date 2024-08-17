# [LeetCode Records](../../README.md) - Question 1364 Number of Trusted Contacts of a Customer

### Attempt 1: Use isin(), groupby(), agg(), and pd.merge()
```py
import pandas as pd

def count_trusted_contacts(customers: pd.DataFrame, contacts: pd.DataFrame, invoices: pd.DataFrame) -> pd.DataFrame:
    contacts['trusted_contacts_cnt'] = contacts['contact_email'].isin(customers['email'])
    counts = contacts.groupby('user_id')[['user_id', 'trusted_contacts_cnt']].agg({'user_id': 'count', 'trusted_contacts_cnt': 'sum'}).rename(columns={'user_id': 'contacts_cnt'}).reset_index()
    counts = pd.merge(customers, counts, left_on='customer_id', right_on='user_id', how='outer')[['customer_id', 'customer_name', 'contacts_cnt', 'trusted_contacts_cnt']]

    return pd.merge(invoices, counts, left_on='user_id', right_on='customer_id').fillna(0)[['invoice_id', 'customer_name', 'price', 'contacts_cnt', 'trusted_contacts_cnt']].sort_values('invoice_id')
```
- Runtime: 462 ms (Beats: 100.00%)
- Memory: 72.08 MB (Beats: 54.72%)

<br>
