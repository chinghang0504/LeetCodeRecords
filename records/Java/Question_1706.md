# [LeetCode Records](../../README.md) - Question 1706 Where Will the Ball Fall

### Attempt 1: Check the next grid in each row
```java
class Solution {
    public int[] findBall(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[] ans = new int[n];

        for (int i = 0; i < n; i++) {
            ans[i] = getResult(grid, m, n, i);
        }

        return ans;
    }

    private int getResult(int[][] grid, int m, int n, int j) {
        for (int i = 0; i < m; i++) {
            if (grid[i][j] == 1) {
                if (j + 1 >= n || grid[i][j + 1] == -1) {
                    return -1;
                }
                j++;
            } else {
                if (j - 1 < 0 || grid[i][j - 1] == 1) {
                    return -1;
                }
                j--;
            }
        }
        
        return j;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.99 MB (Beats: 96.58%)

<br>
