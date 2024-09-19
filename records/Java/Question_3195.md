# [LeetCode Records](../../README.md) - Question 3195 Find the Minimum Area to Cover All Ones I

### Attempt 1: Find the start of i & j and the end of i & j
```java
class Solution {
    public int minimumArea(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;

        int startI = -1;
        for (int i = 0; i < m && startI == -1; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1) {
                    startI = i;
                    break;
                }
            }
        }

        int endI = -1;
        for (int i = m - 1; i >= 0 && endI == -1; i--) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1) {
                    endI = i;
                    break;
                }
            }
        }

        int startJ = -1;
        for (int j = 0; j < n && startJ == -1; j++) {
            for (int i = 0; i < m; i++) {
                if (grid[i][j] == 1) {
                    startJ = j;
                    break;
                }
            }
        }

        int endJ = -1;
        for (int j = n - 1; j >= 0 && endJ == -1; j--) {
            for (int i = 0; i < m; i++) {
                if (grid[i][j] == 1) {
                    endJ = j;
                    break;
                }
            }
        }

        return (endI - startI + 1) * (endJ - startJ + 1);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 196.96 MB (Beats: 34.59%)

<br>
