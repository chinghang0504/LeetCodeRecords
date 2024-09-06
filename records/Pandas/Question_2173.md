# [LeetCode Records](../../README.md) - Question 2173 Longest Winning Streak

### Attempt 1: Use apply() to get the longest streak
```py
import pandas as pd

def get_longest_streak(df):
    curr_value = 0
    max_value = 0
    
    for result in df['result']:
        if result == 'Win':
            curr_value = curr_value + 1
            max_value = max(max_value, curr_value)
        else:
            curr_value = 0
            
    return max_value


def longest_winning_streak(matches: pd.DataFrame) -> pd.DataFrame:
    sorted_matches = matches.sort_values(['player_id', 'match_day'])
    return sorted_matches.groupby('player_id').apply(get_longest_streak).rename('longest_streak').reset_index()
```
- Runtime: 386 ms (Beats: 100.00%)
- Memory: 71.40 MB (Beats: 82.61%)

<br>
