# [LeetCode Records](../../README.md) - Question 3230 Customer Purchasing Behavior Analysis

### Attempt 1: Use pd.merge(), groupby(), agg(), apply(), Decimal(), str(), quantize(), value_counts(), max(), sort_values(), and last()
```py
import pandas as pd
from decimal import Decimal, ROUND_HALF_UP

def analyze_customer_behavior(transactions: pd.DataFrame, products: pd.DataFrame) -> pd.DataFrame:
    transactions = pd.merge(transactions, products, on='product_id')
    ans = transactions.groupby('customer_id').agg(
        total_amount=('amount', 'sum'),
        transaction_count=('transaction_id', 'count'),
        unique_categories=('category', 'nunique'),
        avg_transaction_amount=('amount', 'mean')
    ).reset_index()
    ans['total_amount'] = ans['total_amount'].apply(lambda x: Decimal(str(x)).quantize(Decimal('0.01'), rounding=ROUND_HALF_UP))
    ans['avg_transaction_amount'] = ans['avg_transaction_amount'].apply(lambda x: Decimal(str(x)).quantize(Decimal('0.01'), rounding=ROUND_HALF_UP))
    ans['loyalty_score'] = (ans['transaction_count'] * 10 + ans['total_amount'] / 100).apply(lambda x: Decimal(str(x)).quantize(Decimal('0.01'), rounding=ROUND_HALF_UP))

    category_counts = transactions.groupby('customer_id')['category'].value_counts().reset_index()
    max_category_counts = category_counts.groupby('customer_id')['count'].max().reset_index()
    max_category_counts = pd.merge(category_counts, max_category_counts, on=['customer_id', 'count'])
    merged_df = pd.merge(transactions, max_category_counts, on=['customer_id', 'category'])
    merged_df = merged_df.sort_values(['customer_id', 'transaction_date'])
    top_categories = merged_df.groupby('customer_id')['category'].last().rename('top_category').reset_index()

    ans = pd.merge(ans, top_categories, on='customer_id')
    ans = ans.sort_values(['loyalty_score', 'customer_id'], ascending=[False, True])
    return ans[['customer_id', 'total_amount', 'transaction_count', 'unique_categories', 'avg_transaction_amount', 'top_category', 'loyalty_score']]
```
- Runtime: 488 ms (Beats: 75.47%)
- Memory: 72.50 MB (Beats: 33.96%)

<br>
