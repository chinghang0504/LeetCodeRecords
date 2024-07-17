# [LeetCode Records](../../README.md) - Question 2319 Check if Matrix Is X-Matrix

### Attempt 1: Use a nested loop to check every entry
```java
class Solution {
    public boolean checkXMatrix(int[][] grid) {
        int n = grid.length;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if ((i == j) || (i == n - 1 - j)) {
                    if (grid[i][j] == 0) {
                        return false;
                    }
                } else {
                    if (grid[i][j] != 0) {
                        return false;
                    }
                }
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 92.62%)
- Memory: 45.16 MB (Beats: 64.27%)

<br>
