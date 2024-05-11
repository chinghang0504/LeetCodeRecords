# [LeetCode Records](../../README.md) - Question 311 Sparse Matrix Multiplication

### Attempt 1: 
```java
class Solution {
    public int[][] multiply(int[][] mat1, int[][] mat2) {
        int m = mat1.length;
        int l = mat1[0].length;
        int n = mat2[0].length;
        int[][] result = new int[m][n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                for (int k = 0; k < l; k++) {
                    result[i][j] += mat1[i][k] * mat2[k][j];
                }
            }
        }

        return result;
    }
}
```
- Runtime: 4 ms (Beats: 23.80%)
- Memory: 44.14 MB (Beats: 93.86%)

<br>
