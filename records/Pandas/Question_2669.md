# [LeetCode Records](../../README.md) - Question 2669 Count Artist Occurrences On Spotify Ranking List

### Attempt 1: Use groupby() and size()
```py
import pandas as pd

def count_occurrences(spotify: pd.DataFrame) -> pd.DataFrame:
    return spotify.groupby('artist').size().rename('occurrences').reset_index().sort_values(['occurrences', 'artist'], ascending=[False, True])
```
- Runtime: 396 ms (Beats: 100.00%)
- Memory: 66.86 MB (Beats: 5.00%)

<br>
