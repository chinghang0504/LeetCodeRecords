# [LeetCode Records](../../README.md) - Question 566 Reshape the Matrix

### Attempt 1: 
```java
class Solution {
    public int[][] matrixReshape(int[][] mat, int r, int c) {
        int m = mat.length;
        int n = mat[0].length;

        if (m * n != r * c) {
            return mat;
        }

        int[][] reshapedMatrix = new int[r][c];
        int a = 0, b = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++, b++) {
                if (b == c) {
                    b = 0;
                    a++;
                }
                reshapedMatrix[a][b] = mat[i][j];
            }
        }

        return reshapedMatrix;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.21 MB (Beats: 53.29%)

<br>
