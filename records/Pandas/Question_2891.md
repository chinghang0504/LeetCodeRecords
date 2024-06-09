# [LeetCode Records](../../README.md) - Question 2891 Method Chaining

### Attempt 1: Use sort_values()
```py
import pandas as pd

def findHeavyAnimals(animals: pd.DataFrame) -> pd.DataFrame:
    return animals[animals['weight'] > 100].sort_values('weight', ascending=False)[['name']]
```
- Runtime: 398 ms (Beats: 98.31%)
- Memory: 65.95 MB (Beats: 50.67%)

<br>
