# [LeetCode Records](../../README.md) - Question 1219 Path with Maximum Gold

### Attempt 1: Use recursion to search the next gold position
```java
class Solution {

    private int m;
    private int n;
    private int[][] grid;
    private int maxGold;

    public int getMaximumGold(int[][] grid) {
        m = grid.length;
        n = grid[0].length;
        this.grid = grid;
        maxGold = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] > 0) {
                    getMaximumGoldRecursion(i, j, 0);
                }
            }
        }

        return maxGold;
    }

    private void getMaximumGoldRecursion(int currI, int currJ, int currGold) {
        if (currI < 0 || currI >= m || currJ < 0 || currJ >= n || grid[currI][currJ] == 0) {
            return;
        }

        int gold = grid[currI][currJ];
        currGold += gold;
        maxGold = Math.max(maxGold, currGold);
        grid[currI][currJ] = 0;

        getMaximumGoldRecursion(currI - 1, currJ, currGold);
        getMaximumGoldRecursion(currI + 1, currJ, currGold);
        getMaximumGoldRecursion(currI, currJ - 1, currGold);
        getMaximumGoldRecursion(currI, currJ + 1, currGold);

        grid[currI][currJ] = gold;
    }
}
```
- Runtime: 55 ms (Beats: 92.63%)
- Memory: 40.96 MB (Beats: 78.99%)

<br>
