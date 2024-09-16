# [LeetCode Records](../../README.md) - Question 3239 Minimum Number of Flips to Make Binary Grid Palindromic I

### Attempt 1: Count the number of different entries for each row and for each column
```java
class Solution {
    public int minFlips(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int rowDiffCount = 0;
        int colDiffCount = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n / 2; j++) {
                if (grid[i][j] != grid[i][n - j - 1]) {
                    rowDiffCount++;
                }
            }
        }

        for (int j = 0; j < n; j++) {
            for (int i = 0; i < m / 2; i++) {
                if (grid[i][j] != grid[m - i - 1][j]) {
                    colDiffCount++;
                }
            }
        }

        return Math.min(rowDiffCount, colDiffCount);
    }
}
```
- Runtime: 8 ms (Beats: 60.00%)
- Memory: 110.75 MB (Beats: 59.29%)

<br>
