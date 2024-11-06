# [LeetCode Records](../../README.md) - Question 1267 Count Servers that Communicate

### Attempt 1: Count the number of servers in each row and column
```java
class Solution {
    public int countServers(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[] rowCounts = new int[m];
        int[] colCounts = new int[n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1) {
                    rowCounts[i]++;
                    colCounts[j]++;
                }
            }
        }

        int count = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1 && (rowCounts[i] > 1 || colCounts[j] > 1)) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 51.93 MB (Beats: 78.85%)

<br>
