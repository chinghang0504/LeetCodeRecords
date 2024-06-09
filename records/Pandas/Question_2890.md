# [LeetCode Records](../../README.md) - Question 2890 Reshape Data: Melt

### Attempt 1: Use melt()
```py
import pandas as pd

def meltTable(report: pd.DataFrame) -> pd.DataFrame:
    return pd.melt(report, id_vars=['product'], value_vars=['quarter_1', 'quarter_2', 'quarter_3', 'quarter_4'], var_name='quarter', value_name='sales')
```
- Runtime: 416 ms (Beats: 98.52%)
- Memory: 65.68 MB (Beats: 63.72%)

<br>
