# [LeetCode Records](../../README.md) - Question 2026 Low-Quality Problems

### Attempt 1: 
```py
import pandas as pd

def low_quality_problems(problems: pd.DataFrame) -> pd.DataFrame:
    problems['percentage'] = problems['likes'] / (problems['likes'] + problems['dislikes'])
    return problems[problems['percentage'] < 0.6][['problem_id']].sort_values('problem_id')
```
- Runtime: 420 ms (Beats: 100.00%)
- Memory: 67.36 MB (Beats: 13.04%)

<br>
