# [LeetCode Records](../../README.md) - Question 3358 Books with NULL Ratings

### Attempt 1: Use isna() to find the ratings that are not null
```py
import pandas as pd

def find_unrated_books(books: pd.DataFrame) -> pd.DataFrame:
    ans = books[books['rating'].isna()]
    ans = ans.sort_values('book_id')
    return ans[['book_id', 'title', 'author', 'published_year']]
```
- Runtime: 301 ms (Beats: -%)
- Memory: 69.80 MB (Beats: -%)

<br>
