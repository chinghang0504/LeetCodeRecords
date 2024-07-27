# [LeetCode Records](../../README.md) - Question 3142 Check if Grid Satisfies Conditions

### Attempt 1: Use two nested loop
```java
class Solution {
    public boolean satisfiesConditions(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n - 1; j++) {
                if (grid[i][j] == grid[i][j + 1]) {
                    return false;
                }
            }
        }

        for (int j = 0; j < n; j++) {
            for (int i = 0; i < m - 1; i++) {
                if (grid[i][j] != grid[i + 1][j]) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 92.55%)
- Memory: 44.05 MB (Beats: 77.33%)

<br>
