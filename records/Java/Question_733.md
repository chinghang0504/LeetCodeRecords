# [LeetCode Records](../../README.md) - Question 733 Flood Fill

### Attempt 1: Use a recursive function to find the target neighbours
```java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int color) {
        int m = image.length;
        int n = image[0].length;
        int target = image[sr][sc];
        boolean[][] colored = new boolean[m][n];

        findNeighbour(image, m, n, target, sr, sc, colored);

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (colored[i][j]) {
                    image[i][j] = color;
                }
            }
        }

        return image;
    }

    private void findNeighbour(int[][] image, int m, int n, int target, int startI, int startJ, boolean[][] colored) {
        if (startI < 0 || startI >= m || startJ < 0 || startJ >= n) {
            return;
        } else if (image[startI][startJ] != target) {
            return;
        }

        colored[startI][startJ] = true;
        
        if (startI - 1 >= 0 && image[startI - 1][startJ] == target && !colored[startI - 1][startJ]) {
            colored[startI - 1][startJ] = true;
            findNeighbour(image, m, n, target, startI - 1, startJ, colored);
        }
        if (startI + 1 < m && image[startI + 1][startJ] == target && !colored[startI + 1][startJ]) {
            colored[startI + 1][startJ] = true;
            findNeighbour(image, m, n, target, startI + 1, startJ, colored);
        }
        if (startJ - 1 >= 0 && image[startI][startJ - 1] == target && !colored[startI][startJ - 1]) {
            colored[startI][startJ - 1] = true;
            findNeighbour(image, m, n, target, startI, startJ - 1, colored);
        }
        if (startJ + 1 < n && image[startI][startJ + 1] == target && !colored[startI][startJ + 1]) {
            colored[startI][startJ + 1] = true;
            findNeighbour(image, m, n, target, startI, startJ + 1, colored);
        }
    }
}
```
- Runtime: 1 ms (Beats: 45.13%)
- Memory: 44.87 MB (Beats: 46.68%)

<br>
