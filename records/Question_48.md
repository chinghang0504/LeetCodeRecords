# [LeetCode Records](../README.md) - Question 48 Rotate Image

### Attempt 1: Get the transpose and then reverse the column
```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;

        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }

        for (int j = 0; j < n / 2; j++) {
            for (int i = 0; i < n; i++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[i][n - j - 1];
                matrix[i][n - j - 1] = temp;
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.79 MB (Beats: 91.36%)

<br>
