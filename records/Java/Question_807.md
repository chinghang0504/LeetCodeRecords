# [LeetCode Records](../../README.md) - Question 807 Max Increase to Keep City Skyline

### Attempt 1: Calculate the maximum row and column heights
```java
class Solution {
    public int maxIncreaseKeepingSkyline(int[][] grid) {
        int n = grid.length;
        int[] maxRowHeights = new int[n];
        int[] maxColHieghts = new int[n];

        for (int i = 0; i < n; i++) {
            int maxRowHeight = grid[i][0];
            for (int j = 1; j < n; j++) {
                maxRowHeight = Math.max(maxRowHeight, grid[i][j]);
            }
            maxRowHeights[i] = maxRowHeight;
        }

        for (int j = 0; j < n; j++) {
            int maxColHeight = grid[0][j];
            for (int i = 1; i < n; i++) {
                maxColHeight = Math.max(maxColHeight, grid[i][j]);
            }
            maxColHieghts[j] = maxColHeight;
        }

        int sum = 0;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                sum += Math.min(maxRowHeights[i], maxColHieghts[j]) - grid[i][j];
            }
        }

        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 48.62%)
- Memory: 44.06 MB (Beats: 54.48%)

<br>
