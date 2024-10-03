# [LeetCode Records](../../README.md) - Question 1020 Number of Enclaves

### Attempt 1: Use recursion to check the boundary
```java
class Solution {

    private int m;
    private int n;
    private int[][] grid;

    public int numEnclaves(int[][] grid) {
        m = grid.length;
        n = grid[0].length;
        this.grid = grid;

        for (int j = 0; j < n; j++) {
            checkBoundary(0, j);
            checkBoundary(m - 1, j);
        }
        for (int i = 1; i < m - 1; i++) {
            checkBoundary(i, 0);
            checkBoundary(i, n - 1);
        }

        int count = 0;

        for (int i = 1; i < m - 1; i++) {
            for (int j = 1; j < n - 1; j++) {
                if (grid[i][j] == 1) {
                    count++;
                }
            }
        }

        return count;
    }

    private void checkBoundary(int startI, int startJ) {
        if (startI < 0 || startI >= m || startJ < 0 || startJ >= n || grid[startI][startJ] != 1) {
            return;
        }

        grid[startI][startJ] = 0;
        checkBoundary(startI - 1, startJ);
        checkBoundary(startI + 1, startJ);
        checkBoundary(startI, startJ - 1);
        checkBoundary(startI, startJ + 1);
    }
}
```
- Runtime: 6 ms (Beats: 98.06%)
- Memory: 55.16 MB (Beats: 67.72%)

<br>
