# [LeetCode Records](../../README.md) - Question 304 Range Sum Query 2D - Immutable

### Attempt 1: Use one-dimensional cumulative sum
```java
class NumMatrix {

    private int m;
    private int n;
    private int[][] cumsumMatrix;

    public NumMatrix(int[][] matrix) {
        m = matrix.length;
        n = matrix[0].length;
        cumsumMatrix = new int[m][n];

        for (int i = 0; i < m; i++) {
            int cumsum = 0;
            for (int j = 0; j < n; j++) {
                cumsum += matrix[i][j];
                cumsumMatrix[i][j] = cumsum;
            }
        }
    }

    public int sumRegion(int row1, int col1, int row2, int col2) {
        int sum = 0;

        if (col1 == 0) {
            for (int i = row1; i <= row2; i++) {
                sum += cumsumMatrix[i][col2];
            }
        } else {
            for (int i = row1; i <= row2; i++) {
                sum += cumsumMatrix[i][col2] - cumsumMatrix[i][col1 - 1];
            }
        }

        return sum;
    }
}

/**
 * Your NumMatrix object will be instantiated and called as such:
 * NumMatrix obj = new NumMatrix(matrix);
 * int param_1 = obj.sumRegion(row1,col1,row2,col2);
 */
```
- Runtime: 114 ms (Beats: 25.00%)
- Memory: 70.05 MB (Beats: 59.67%)

<br>
