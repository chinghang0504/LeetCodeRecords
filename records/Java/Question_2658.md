# [LeetCode Records](../../README.md) - Question 2658 Maximum Number of Fish in a Grid

### Attempt 1: Use recursion to search adjacent water cell
```java
class Solution {
    public int findMaxFish(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int maxFishNum = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] != 0) {
                    maxFishNum = Math.max(maxFishNum, getFishNum(m, n, grid, i, j));
                }
            }
        }

        return maxFishNum;
    }

    private int getFishNum(int m, int n, int[][] grid, int centerI, int centerJ) {
        if (centerI < 0 || centerI >= m || centerJ < 0 || centerJ >= n || grid[centerI][centerJ] == 0) {
            return 0;
        }
        
        int sum = grid[centerI][centerJ];
        grid[centerI][centerJ] = 0;

        sum += getFishNum(m, n, grid, centerI - 1, centerJ);
        sum += getFishNum(m, n, grid, centerI + 1, centerJ);
        sum += getFishNum(m, n, grid, centerI, centerJ - 1);
        sum += getFishNum(m, n, grid, centerI, centerJ + 1);

        return sum;
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 44.88 MB (Beats: 55.45%)

<br>
