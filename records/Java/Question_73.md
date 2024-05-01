# [LeetCode Records](../../README.md) - Question 73 Set Matrix Zeroes

### Attempt 1: Use two boolean arrays to record which rows and columns needed to set zeros

```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length;;
        int n = matrix[0].length;
        boolean[] rows = new boolean[m];
        boolean[] cols = new boolean[n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] == 0) {
                    rows[i] = true;
                    cols[j] = true;
                }
            }
        }

        for (int i = 0; i < m; i++) {
            if (rows[i]) {
                for (int j = 0; j < n; j++) {
                    matrix[i][j] = 0;
                }
            }
        }
        for (int j = 0; j < n; j++) {
            if (cols[j]) {
                for (int i = 0; i < m; i++) {
                    matrix[i][j] = 0;
                }
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.47 MB (Beats: 58.33%)

<br>
