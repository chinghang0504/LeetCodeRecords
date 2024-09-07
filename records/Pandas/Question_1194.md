# [LeetCode Records](../../README.md) - Question 1194 Tournament Winners

### Attempt 1: Use pd.concat() to get all the player scores
```py
import pandas as pd

def tournament_winners(players: pd.DataFrame, matches: pd.DataFrame) -> pd.DataFrame:
    first_player_scores = matches[['first_player', 'first_score']].rename(columns={'first_player': 'player_id', 'first_score': 'score'})
    second_player_scores = matches[['second_player', 'second_score']].rename(columns={'second_player': 'player_id', 'second_score': 'score'})

    scores = pd.concat([first_player_scores, second_player_scores])
    scores = scores.groupby('player_id')['score'].sum().reset_index()

    merged_df = pd.merge(players, scores, on='player_id')
    merged_df = merged_df.sort_values(['group_id', 'score', 'player_id'], ascending=[True, False, True])

    ans = merged_df.loc[merged_df.groupby('group_id')['score'].idxmax()]
    return ans[['group_id', 'player_id']]
```
- Runtime: 427 ms (Beats: 82.14%)
- Memory: 72.39 MB (Beats: 78.57%)

<br>
