# [LeetCode Records](../../README.md) - Question 867 Transpose Matrix

### Attempt 1: 
```java
class Solution {
    public int[][] transpose(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        int[][] result = new int[n][m];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                result[j][i] = matrix[i][j];
            }
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.02 MB (Beats: 8.89%)

<br>
