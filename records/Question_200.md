# [LeetCode Records](../README.md) - Question 200 Number of Islands

### Attempt 1: Remove the adjacent island
```java
class Solution {
    public int numIslands(char[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int count = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == '1') {
                    count++;
                    removeIsland(grid, m, n, i, j);
                }
            }
        }

        return count;
    }

    private void removeIsland(char[][] grid, int m, int n, int start_i, int start_j) {
        List<Coordinates> prevSaved = new ArrayList<>();
        prevSaved.add(new Coordinates(start_i, start_j));

        while (!prevSaved.isEmpty()) {
            List<Coordinates> saved = new ArrayList<>();

            for (Coordinates c : prevSaved) {
                if (c.i < 0 || c.i >= m || c.j < 0 || c.j >= n) {
                    continue;
                }

                if (grid[c.i][c.j] == '1') {
                    grid[c.i][c.j] = '0';

                    saved.add(new Coordinates(c.i, c.j - 1));
                    saved.add(new Coordinates(c.i, c.j + 1));
                    saved.add(new Coordinates(c.i - 1, c.j));
                    saved.add(new Coordinates(c.i + 1, c.j));
                }
            }

            prevSaved = saved;
        }
    }

    private static class Coordinates {
        int i, j;

        Coordinates(int i, int j) {
            this.i = i;
            this.j = j;
        }
    }
}
```
- Runtime: 8 ms (Beats: 15.07%)
- Memory: 51.94 MB (Beats: 16.94%)

<br>
