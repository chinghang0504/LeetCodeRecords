# [LeetCode Records](../../README.md) - Question 2482 Difference Between Ones and Zeros in Row and Column

### Attempt 1: Calculate the number of ones in rows and columns
```java
class Solution {
    public int[][] onesMinusZeros(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[] onesRow = new int[m];
        int[] onesCol = new int[n];
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                onesRow[i] += grid[i][j];
            }
        }

        for (int j = 0; j < n; j++) {
            for (int i = 0; i < m; i++) {
                onesCol[j] += grid[i][j];
            }
        }

        int[][] answer = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                answer[i][j] = onesRow[i] + onesCol[j] - (m - onesRow[i]) - (n - onesCol[j]);
            }
        }

        return answer;
    }
}
```
- Runtime: 10 ms (Beats: 65.63%)
- Memory: 84.88 MB (Beats: 51.88%)

<br>
