# [LeetCode Records](../../README.md) - Question 221 Maximal Square

### Attempt 1: Create a function to check the square with a specific length
```java
class Solution {

    private int m;
    private int n;
    private char[][] matrix;

    public int maximalSquare(char[][] matrix) {
        this.m = matrix.length;
        this.n = matrix[0].length;
        this.matrix = matrix;
        int maxLength = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                while (isSquare(i, j, maxLength + 1)) {
                    maxLength++;
                }
            }
        }

        return maxLength * maxLength;
    }

    private boolean isSquare(int startI, int startJ, int length) {
        int endI = startI + length;
        int endJ = startJ + length;
        if (endI > m || endJ > n) {
            return false;
        }

        for (int i = startI; i < endI; i++) {
            for (int j = startJ; j < endJ; j++) {
                if (matrix[i][j] == '0') {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 41 ms (Beats: 10.31%)
- Memory: 56.22 MB (Beats: 86.96%)

<br>
