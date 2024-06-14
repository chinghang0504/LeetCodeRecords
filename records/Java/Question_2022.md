# [LeetCode Records](../../README.md) - Question 2022 Convert 1D Array Into 2D Array

### Attempt 1: Use two loops
```java
class Solution {
    public int[][] construct2DArray(int[] original, int m, int n) {
        if (original.length != m * n) {
            return new int[0][0];
        }

        int[][] result = new int[m][n];
        int curr = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                result[i][j] = original[curr];
                curr++;
            }
        }

        return result;
    }
}
```
- Runtime: 4 ms (Beats: 62.32%)
- Memory: 54.86 MB (Beats: 98.57%)

<br>
