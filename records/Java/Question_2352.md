# [LeetCode Records](../../README.md) - Question 2352 Equal Row and Column Pairs

### Attempt 1: Test every combination of row and column
```java
class Solution {
    public int equalPairs(int[][] grid) {
        int n = grid.length;
        int count = 0;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (isEqual(grid, n, i, j)) {
                    count++;
                }
            }
        }

        return count;
    }

    private boolean isEqual(int[][] grid, int n, int row, int col) {
        for (int i = 0; i < n; i++) {
            if (grid[row][i] != grid[i][col]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 29 ms (Beats: 63.44%)
- Memory: 47.55 MB (Beats: 87.74%)

<br>
