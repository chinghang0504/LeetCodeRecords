# [LeetCode Records](../../README.md) - Question 3033 Modify the Matrix

### Attempt 1: Use a nested loop
```java
class Solution {
    public int[][] modifiedMatrix(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        int[][] answer = new int[m][n];

        for (int j = 0; j < n; j++) {
            int max = matrix[0][j];
            for (int i = 1; i < m; i++) {
                max = Math.max(max, matrix[i][j]);
            }

            for (int i = 0; i < m; i++) {
                answer[i][j] = matrix[i][j] == -1 ? max : matrix[i][j];
            }
        }
        
        return answer;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.39 MB (Beats: 55.49%)

<br>
