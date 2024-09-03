# [LeetCode Records](../../README.md) - Question 3052 Maximize Items

### Attempt 1: Get the total count and total square footage of prime and not prime items first
```py
import pandas as pd

def maximize_items(inventory: pd.DataFrame) -> pd.DataFrame:
    total_inventory = inventory.groupby('item_type').agg(
        total_count=('item_id', 'count'),
        total_square_footage=('square_footage', 'sum')
    ).reset_index()

    prime_total_count = total_inventory[total_inventory['item_type'] == 'prime_eligible'].iloc[0]['total_count']
    prime_total_square_footage = total_inventory[total_inventory['item_type'] == 'prime_eligible'].iloc[0]['total_square_footage']
    not_prime_total_count = total_inventory[total_inventory['item_type'] == 'not_prime'].iloc[0]['total_count']
    not_prime_total_square_footage = total_inventory[total_inventory['item_type'] == 'not_prime'].iloc[0]['total_square_footage']

    prime_item_count = 500000 // prime_total_square_footage
    remaining_square_footage = 500000 - prime_item_count * prime_total_square_footage
    not_prime_item_count = remaining_square_footage // not_prime_total_square_footage

    return pd.DataFrame({
        'item_type': ['prime_eligible', 'not_prime'],
        'item_count': [prime_item_count * prime_total_count, not_prime_item_count * not_prime_total_count],
    }).sort_values('item_count', ascending=False)
```
- Runtime: 362 ms (Beats: 70.00%)
- Memory: 70.90 MB (Beats: 10.00%)

<br>
