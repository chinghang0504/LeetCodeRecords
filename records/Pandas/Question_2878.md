# [LeetCode Records](../../README.md) - Question 2878 Get the Size of a DataFrame

### Attempt 1: Use shape
```py
import pandas as pd

def getDataframeSize(players: pd.DataFrame) -> List[int]:
    return list(players.shape)
```
- Runtime: 366 ms (Beats: 99.28%)
- Memory: 65.60 MB (Beats: 26.77%)

<br>
