# [LeetCode Records](../../README.md) - Question 2373 Largest Local Values in a Matrix

### Attempt 1: Use a nested loop and a helper function which has a nested loop
```java
class Solution {
    public int[][] largestLocal(int[][] grid) {
        int n = grid.length;
        int m = n - 2;
        int[][] result = new int[m][m];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < m; j++) {
                result[i][j] = getLocalMax(grid, i, j);
            }
        }

        return result;
    }

    private int getLocalMax(int[][] grid, int startI, int startJ) {
        int max = grid[startI][startJ];

        for (int i = startI; i < startI + 3; i++) {
            for (int j = startJ; j < startJ + 3; j++) {
                max = Math.max(max, grid[i][j]);
            }
        }

        return max;
    }
}
```
- Runtime: 2 ms (Beats: 99.90%)
- Memory: 45.18 MB (Beats: 92.52%)

<br>
