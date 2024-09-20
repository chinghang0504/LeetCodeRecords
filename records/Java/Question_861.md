# [LeetCode Records](../../README.md) - Question 861 Score After Flipping Matrix

### Attempt 1: Flip row which has a zero in the first column
```java
class Solution {
    public int matrixScore(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;

        for (int i = 0; i < m; i++) {
            if (grid[i][0] == 0) {
                flipRow(grid, n, i);
            }
        }
        
        int targetZeroCount = m / 2 + 1;
        for (int j = 1; j < n; j++) {
            int zeroCount = getZeroCount(grid, m, j);
            if (zeroCount >= targetZeroCount) {
                flipColumn(grid, m, j);
            }
        }

        return getTotalSum(grid, m, n);
    }

    private void flipRow(int[][] grid, int n, int i) {
        for (int j = 0; j < n; j++) {
            grid[i][j] = grid[i][j] == 0 ? 1 : 0;
        }
    }

    private void flipColumn(int[][] grid, int m, int j) {
        for (int i = 0; i < m; i++) {
            grid[i][j] = grid[i][j] == 0 ? 1 : 0;
        }
    }

    private int getZeroCount(int[][] grid, int m, int j) {
        int count = 0;
        for (int i = 0; i < m; i++) {
            if (grid[i][j] == 0) {
                count++;
            }
        }
        return count;
    }

    private int getTotalSum(int[][] grid, int m, int n) {
        int sum = 0;
        for (int i = 0; i < m; i++) {
            int localSum = 0;
            for (int j = 0; j < n; j++) {
                localSum <<= 1;
                localSum += grid[i][j];
            }
            sum += localSum;
        }
        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.72 MB (Beats: 16.15%)

<br>
