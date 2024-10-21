# [LeetCode Records](../../README.md) - Question 130 Surrounded Regions

### Attempt 1: Use a boolean[][] to record the checked entries
```java
class Solution {

    private int m;
    private int n;
    private char[][] board;
    private boolean[][] checked;

    public void solve(char[][] board) {
        this.m = board.length;
        this.n = board[0].length;
        this.board = board;
        this.checked = new boolean[m][n];

        for (int i = 0; i < m; i++) {
            checkCell(i, 0);
            checkCell(i, n - 1);
        }

        for (int j = 1; j < n - 1; j++) {
            checkCell(0, j);
            checkCell(m - 1, j);
        }

        for (int i = 1; i < m - 1; i++) {
            for (int j = 1; j < n - 1; j++) {
                if (!checked[i][j]) {
                    board[i][j] = 'X';
                }
            }
        }
    }

    private void checkCell(int startI, int startJ) {
        if (startI < 0 || startI >= m || startJ < 0 || startJ >= n || checked[startI][startJ] || board[startI][startJ] == 'X') {
            return;
        }

        checked[startI][startJ] = true;

        checkCell(startI - 1, startJ);
        checkCell(startI + 1, startJ);
        checkCell(startI, startJ - 1);
        checkCell(startI, startJ + 1);
    }
}
```
- Runtime: 1 ms (Beats: 99.67%)
- Memory: 45.20 MB (Beats: 63.13%)

<br>
