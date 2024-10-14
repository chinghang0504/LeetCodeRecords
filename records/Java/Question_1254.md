# [LeetCode Records](../../README.md) - Question 1254 Number of Closed Islands

### Attempt 1: Change the opened land to water
```java
class Solution {

    private int m;
    private int n;
    private int[][] grid;

    public int closedIsland(int[][] grid) {
        this.m = grid.length;
        this.n = grid[0].length;
        this.grid = grid;

        for (int j = 1; j < n - 1; j++) {
            if (grid[0][j] == 0) {
                changeLandToWater(0, j);
            }
            if (grid[m - 1][j] == 0) {
                changeLandToWater(m - 1, j);
            }
        }
        for (int i = 0; i < m; i++) {
            if (grid[i][0] == 0) {
                changeLandToWater(i, 0);
            }
            if (grid[i][n - 1] == 0) {
                changeLandToWater(i, n - 1);
            }
        }

        int count = 0;
        for (int i = 1; i < m - 1; i++) {
            for (int j = 1; j < n - 1; j++) {
                if (grid[i][j] == 0) {
                    count++;
                    changeLandToWater(i, j);
                }
            }
        }

        return count;
    }

    private void changeLandToWater(int startI, int startJ) {
        if (startI < 0 || startI >= m || startJ < 0 || startJ >= n || grid[startI][startJ] != 0) {
            return;
        }

        grid[startI][startJ] = 1;

        changeLandToWater(startI - 1, startJ);
        changeLandToWater(startI + 1, startJ);
        changeLandToWater(startI, startJ - 1);
        changeLandToWater(startI, startJ + 1);
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 44.30 MB (Beats: 59.14%)

<br>
