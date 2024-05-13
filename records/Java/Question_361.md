# [LeetCode Records](../../README.md) - Question 361 Bomb Enemy

### Attempt 1: Check every empty place
```java
class Solution {

    private char[][] grid;
    private int m;
    private int n;
    private int max;

    public int maxKilledEnemies(char[][] grid) {
        this.grid = grid;
        this.m = grid.length;
        this.n = grid[0].length;
        this.max = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == '0') {
                    checkBomb(i, j);
                }
            }
        }

        return max;
    }

    private void checkBomb(int row, int col) {
        int count = 0;
        for (int i = row - 1; i >= 0; i--) {
            if (grid[i][col] == 'E') {
                count++;
            } else if (grid[i][col] == 'W') {
                break;
            }
        }
        for (int i = row + 1; i < m; i++) {
            if (grid[i][col] == 'E') {
                count++;
            } else if (grid[i][col] == 'W') {
                break;
            }
        }
        for (int j = col - 1; j >= 0; j--) {
            if (grid[row][j] == 'E') {
                count++;
            } else if (grid[row][j] == 'W') {
                break;
            }
        }
        for (int j = col + 1; j < n; j++) {
            if (grid[row][j] == 'E') {
                count++;
            } else if (grid[row][j] == 'W') {
                break;
            }
        }

        max = Math.max(max, count);
    }
}
```
- Runtime: 220 ms (Beats: 30.87%)
- Memory: 59.28 MB (Beats: 69.80%)

<br>
