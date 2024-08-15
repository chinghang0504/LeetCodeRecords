# [LeetCode Records](../../README.md) - Question 3054 Binary Tree Nodes

### Attempt 1: Use isnull(), assign(), isin(), notnull(), and pd.concat()
```py
import pandas as pd

def binary_tree_nodes(tree: pd.DataFrame) -> pd.DataFrame:
    root = tree[tree['P'].isnull()].assign(Type='Root')

    inner = tree[tree['N'].isin(tree['P'])]
    inner = inner[inner['P'].notnull()].assign(Type='Inner')

    leaf = tree[~tree['N'].isin(tree['P'])]
    leaf = leaf[leaf['P'].notnull()].assign(Type='Leaf')

    return pd.concat([root, inner, leaf])[['N', 'Type']].sort_values('N')
```
- Runtime: 370 ms (Beats: 73.33%)
- Memory: 70.44 MB (Beats: 22.22%)

<br>
