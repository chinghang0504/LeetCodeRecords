# [LeetCode Records](../../README.md) - Question 1582 Special Positions in a Binary Matrix

### Attempt 1: Test every row and column
```java
class Solution {
    public int numSpecial(int[][] mat) {
        int m = mat.length;
        int n = mat[0].length;

        int count = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (mat[i][j] == 1 && isSpecial(mat, m, n, i, j)) {
                    count++;
                }
            }
        }

        return count;
    }

    private boolean isSpecial(int[][] mat, int m, int n, int x, int y) {
        for (int i = 0; i < x; i++) {
            if (mat[i][y] != 0) {
                return false;
            }
        }
        for (int i = x + 1; i < m; i++) {
            if (mat[i][y] != 0) {
                return false;
            }
        }

        for (int j = 0; j < y; j++) {
            if (mat[x][j] != 0) {
                return false;
            }
        }
        for (int j = y + 1; j < n; j++) {
            if (mat[x][j] != 0) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 90.57%)
- Memory: 45.04 MB (Beats: 23.87%)

<br>
