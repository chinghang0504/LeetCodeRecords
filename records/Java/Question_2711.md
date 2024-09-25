# [LeetCode Records](../../README.md) - Question 2711 Difference of Number of Distinct Values on Diagonals

### Attempt 1: Use two HashSet to store the above and below values
```java
class Solution {
    public int[][] differenceOfDistinctValues(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[][] ans = new int[m][n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                ans[i][j] = getDiffNumOfDistinctValues(grid, m, n, i, j);
            }
        }

        return ans;
    }

    private int getDiffNumOfDistinctValues(int[][] grid, int m, int n, int centerI, int centerJ) {
        Set<Integer> aboveValues = new HashSet<>();
        Set<Integer> belowValues = new HashSet<>();

        int currI = centerI - 1;
        int currJ = centerJ - 1;
        while (currI >= 0 && currJ >= 0) {
            aboveValues.add(grid[currI][currJ]);
            currI--;
            currJ--;
        }

        currI = centerI + 1;
        currJ = centerJ + 1;
        while (currI < m && currJ < n) {
            belowValues.add(grid[currI][currJ]);
            currI++;
            currJ++;
        }

        return Math.abs(aboveValues.size() - belowValues.size());
    }
}
```
- Runtime: 21 ms (Beats: 75.31%)
- Memory: 45.33 MB (Beats: 85.19%)

<br>
