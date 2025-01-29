# [LeetCode Records](../../README.md) - Question 1391 Check if There is a Valid Path in a Grid

### Attempt 1: Call a finding path function twice
```java
class Solution {

    // Left: -1, Right: 1, Up: 2, Down: -2
    private int[][] directions = { {-1, 1}, {2, -2}, {-1, -2}, {1, -2}, {2, -1}, {2, 1} };
    private int m;
    private int n;
    private int[][] grid;

    public boolean hasValidPath(int[][] grid) {
        m = grid.length;
        n = grid[0].length;
        this.grid = grid;

        int[] direction = directions[grid[0][0] - 1];
        if (findPath(direction[0])) {
            return true;
        }
        if (findPath(direction[1])) {
            return true;
        }

        return false;
    }

    private boolean findPath(int exit) {
        int i = 0;
        int j = 0;
        while (i != m - 1 || j != n - 1) {
            if (exit == 1) {
                j++;
                if (j >= n) {
                    return false;
                }
            } else if (exit == -1) {
                j--;
                if (j < 0) {
                    return false;
                }
            } else if (exit == 2) {
                i--;
                if (i < 0) {
                    return false;
                }
            } else {
                i++;
                if (i >= m) {
                    return false;
                }
            }

            if (grid[i][j] == 0) {
                return false;
            }

            int[] direction = directions[grid[i][j] - 1];
            if (exit == -1 * direction[0]) {
                exit = direction[1];
            } else if (exit == -1 * direction[1]) {
                exit = direction[0];
            } else {
                return false;
            }

            grid[i][j] = 0;
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 57.42 MB (Beats: 100.00%)

<br>
