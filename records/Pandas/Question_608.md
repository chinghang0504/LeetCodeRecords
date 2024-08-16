# [LeetCode Records](../../README.md) - Question 608 Tree Node

### Attempt 1: Use isnull(), assign(), isin(), notnull(), and pd.concat()
```py
import pandas as pd

def tree_node(tree: pd.DataFrame) -> pd.DataFrame:
    root = tree[tree['p_id'].isnull()].assign(type='Root')

    inner = tree[tree['id'].isin(tree['p_id'])]
    inner = inner[inner['p_id'].notnull()].assign(type='Inner')

    leaf = tree[~tree['id'].isin(tree['p_id'])]
    leaf = leaf[leaf['p_id'].notnull()].assign(type='Leaf')

    return pd.concat([root, inner, leaf])[['id', 'type']]
```
- Runtime: 379 ms (Beats: 84.09%)
- Memory: 70.23 MB (Beats: 17.63%)

<br>
