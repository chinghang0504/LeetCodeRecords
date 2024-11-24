# [LeetCode Records](../../README.md) - Question 2257 Count Unguarded Cells in the Grid

### Attempt 1: Stop when reaching the guard or the wall
```java
class Solution {
    public int countUnguarded(int m, int n, int[][] guards, int[][] walls) {
        int[][] grid = new int[m][n];

        for (int[] wall : walls) {
            grid[wall[0]][wall[1]] = 2;
        }
        for (int[] guard : guards) {
            grid[guard[0]][guard[1]] = 2;
        }

        for (int[] guard : guards) {
            int i = guard[0] - 1;
            int j = guard[1];
            while (i >= 0 && grid[i][j] != 2) {
                grid[i][j] = 1;
                i--;
            }

            i = guard[0] + 1;
            while (i < m && grid[i][j] != 2) {
                grid[i][j] = 1;
                i++;
            }

            i = guard[0];
            j = guard[1] - 1;
            while (j >= 0 && grid[i][j] != 2) {
                grid[i][j] = 1;
                j--;
            }

            j = guard[1] + 1;
            while (j < n && grid[i][j] != 2) {
                grid[i][j] = 1;
                j++;
            }
        }

        int count = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 0) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 17 ms (Beats: 99.89%)
- Memory: 66.86 MB (Beats: 92.81%)

<br>
