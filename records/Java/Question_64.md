# [LeetCode Records](../../README.md) - Question 64 Minimum Path Sum

### Attempt 1: Use an int array to accumulate
```java
class Solution {

    public int minPathSum(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[][] saved = new int[m][n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (i == 0 && j == 0) {
                    saved[i][j] = grid[i][j];
                } else if (i == 0) {
                    saved[i][j] = grid[i][j] + saved[i][j - 1];
                } else if (j == 0) {
                    saved[i][j] = grid[i][j] + saved[i - 1][j];
                } else {
                    saved[i][j] = grid[i][j] + Math.min(saved[i][j - 1], saved[i - 1][j]);
                }
            }
        }

        return saved[m - 1][n - 1];
    }
}
```
- Runtime: 3 ms (Beats: 70.33%)
- Memory: 45.12 MB (Beats: 83.62%)

<br>

### Attempt 2: Use the source array to accumulate
```java
class Solution {

    public int minPathSum(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (i == 0 && j == 0) {
                    continue;
                } else if (i == 0) {
                    grid[i][j] += grid[i][j - 1];
                } else if (j == 0) {
                    grid[i][j] += grid[i - 1][j];
                } else {
                    grid[i][j] += Math.min(grid[i][j - 1], grid[i - 1][j]);
                }
            }
        }

        return grid[m - 1][n - 1];
    }
}
```
- Runtime: 3 ms (Beats: 70.33%)
- Memory: 45.83 MB (Beats: 9.40%)

<br>

### Attempt 3: Remove the if/else statement
```java
class Solution {

    public int minPathSum(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;

        for (int j = 1; j < n; j++) {
            grid[0][j] += grid[0][j - 1];
        }
        for (int i = 1; i < m; i++) {
            grid[i][0] += grid[i - 1][0];
        }
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                grid[i][j] += Math.min(grid[i][j - 1], grid[i - 1][j]);
            }
        }

        return grid[m - 1][n - 1];
    }
}
```
- Runtime: 3 ms (Beats: 70.33%)
- Memory: 45.03 MB (Beats: 91.06%)

<br>
