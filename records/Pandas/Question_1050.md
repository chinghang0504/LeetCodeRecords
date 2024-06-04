# [LeetCode Records](../../README.md) - Question 1050 Actors and Directors Who Cooperated At Least Three Times

### Attempt 1: Use groupby() and count()
```py
import pandas as pd

def actors_and_directors(actor_director: pd.DataFrame) -> pd.DataFrame:
    count_df = actor_director.groupby(['actor_id', 'director_id'])['timestamp'].count()
    return count_df[count_df >= 3].reset_index()[['actor_id', 'director_id']]
```
- Runtime: 513 ms (Beats: 96.59%)
- Memory: 66.75 MB (Beats: 30.80%)

<br>
