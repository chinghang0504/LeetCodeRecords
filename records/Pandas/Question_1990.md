# [LeetCode Records](../../README.md) - Question 1990 Count the Number of Experiments

### Attempt 1: Use groupby(), count(), pd.merge(), and fillna()
```py
import pandas as pd

def count_experiments(experiments: pd.DataFrame) -> pd.DataFrame:
    counts = experiments.groupby(['platform', 'experiment_name'])['experiment_id'].count().rename('num_experiments').reset_index()

    platforms = pd.DataFrame({
        'platform': ['Android','Android','Android','IOS','IOS','IOS','Web','Web','Web'],
        'experiment_name': ['Reading','Sports','Programming','Reading','Sports','Programming','Reading','Sports','Programming'],
    })

    return pd.merge(platforms, counts, on=['platform', 'experiment_name'], how='left').fillna(0)
```
- Runtime: 435 ms (Beats: 93.55%)
- Memory: 71.12 MB (Beats: 61.29%)

<br>
