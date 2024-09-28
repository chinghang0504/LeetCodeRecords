# [LeetCode Records](../../README.md) - Question 959 Regions Cut By Slashes

### Attempt 1: Convert a character to a 3x3 matrix
```java
class Solution {
    public int regionsBySlashes(String[] grid) {
        int m = grid.length * 3;
        int n = grid[0].length() * 3;
        int[][] graph = new int[m][n];

        generateGraph(grid, graph);

        int count = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (graph[i][j] == 0) {
                    count++;
                    colorSection(graph, m, n, i, j);
                }
            }
        }

        return count;
    }

    private void generateGraph(String[] grid, int[][] graph) {
        for (int i = 0; i < grid.length; i++) {
            char[] arr = grid[i].toCharArray();
            for (int j = 0; j < arr.length; j++) {
                if (arr[j] == '/') {
                    graph[i*3][j*3+2] = 1;
                    graph[i*3+1][j*3+1] = 1;
                    graph[i*3+2][j*3] = 1;
                } else if (arr[j] == '\\') {
                    graph[i*3][j*3] = 1;
                    graph[i*3+1][j*3+1] = 1;
                    graph[i*3+2][j*3+2] = 1;
                }
            }
        }
    }

    private void colorSection(int[][] graph, int m, int n, int startI, int startJ) {
        if (startI < 0 || startJ < 0 || startI >= m || startJ >= n || graph[startI][startJ] != 0) {
            return;
        }

        graph[startI][startJ] = 1;

        colorSection(graph, m, n, startI - 1, startJ);
        colorSection(graph, m, n, startI + 1, startJ);
        colorSection(graph, m, n, startI, startJ - 1);
        colorSection(graph, m, n, startI, startJ + 1);
    }
}
```
- Runtime: 8 ms (Beats: 38.69%)
- Memory: 43.12 MB (Beats: 20.23%)

<br>
