# [LeetCode Records](../../README.md) - Question 54 Spiral Matrix

### Attempt 1: Use a boolean[] to record the entries is reached
```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;

        if (m * n == 1) {
            return List.of(matrix[0][0]);
        }

        boolean[][] reached = new boolean[m][n];
        List<Integer> ans = new ArrayList<>();
        int i = 0;
        int j = 0;
        int direction = 0;
        while (true) {
            reached[i][j] = true;
            ans.add(matrix[i][j]);

            int nextI = i;
            int nextJ = j;
            
            // Go right
            if (direction == 0) {
                nextJ = j + 1;
                if (nextJ >= n || reached[nextI][nextJ]) {
                    nextJ = j;
                    nextI = i + 1;
                    direction = 1;
                }
            } 
            // Go down
            else if (direction == 1) {
                nextI = i + 1;
                if (nextI >= m || reached[nextI][nextJ]) {
                    nextI = i;
                    nextJ = j - 1;
                    direction = 2;
                }
            } 
            // Go left
            else if (direction == 2) {
                nextJ = j - 1;
                if (nextJ < 0 || reached[nextI][nextJ]) {
                    nextJ = j;
                    nextI = i - 1;
                    direction = 3;
                }
            } 
            // Go up
            else if (direction == 3) {
                nextI = i - 1;
                if (nextI < 0 || reached[nextI][nextJ]) {
                    nextI = i;
                    nextJ = j + 1;
                    direction = 0;
                }
            }

            if (nextI < 0 || nextJ < 0 || nextI >= m || nextJ >= n || reached[nextI][nextJ]) {
                return ans;
            } else {
                i = nextI;
                j = nextJ; 
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.20 MB (Beats: 81.40%)

<br>
