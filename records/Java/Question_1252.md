# [LeetCode Records](../../README.md) - Question 1252 Cells with Odd Values in a Matrix

### Attempt 1: Count all the values
```java
class Solution {
    public int oddCells(int m, int n, int[][] indices) {
        int[][] matrix = new int[m][n];

        for (int[] point : indices) {
            for (int j = 0; j < n; j++) {
                matrix[point[0]][j]++;
            }
            for (int i = 0; i < m; i++) {
                matrix[i][point[1]]++;
            }
        }

        int count = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] % 2 == 1) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 54.49%)
- Memory: 41.14 MB (Beats: 89.92%)

<br>

### Attempt 2: Use row and column counts
```java
class Solution {
    public int oddCells(int m, int n, int[][] indices) {
        int[] rowCounts = new int[m];
        int[] colCounts = new int[n];

        for (int[] point : indices) {
            rowCounts[point[0]]++;
            colCounts[point[1]]++;
        }

        int count = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if ((rowCounts[i] + colCounts[j]) % 2 == 1) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 91.10%)
- Memory: 41.37 MB (Beats: 70.95%)

<br>
