# [LeetCode Records](../../README.md) - Question 289 Game of Life

### Attempt 1: Calculate every entry
```java
class Solution {

    public void gameOfLife(int[][] board) {
        int m = board.length;
        int n = board[0].length;
        int[][] nextBoard = new int[m][n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                nextBoard[i][j] = getNextState(board, m, n, i, j);
            }
        }

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                board[i][j] = nextBoard[i][j];
            }
        }
    }

    private int getNextState(int[][] board, int m, int n, int i, int j) {
        int count = 0;
        if (i - 1 >= 0) {
            count += board[i - 1][j];

            if (j - 1 >= 0) {
                count += board[i - 1][j - 1];
            }
            if (j + 1 < n) {
                count += board[i - 1][j + 1];
            }
        }
        if (j - 1 >= 0) {
            count += board[i][j - 1];
        }
        if (j + 1 < n) {
            count += board[i][j + 1];
        }
        if (i + 1 < m) {
            count += board[i + 1][j];

            if (j - 1 >= 0) {
                count += board[i + 1][j - 1];
            }
            if (j + 1 < n) {
                count += board[i + 1][j + 1];
            }
        }

        if (board[i][j] == 1) {
            return count < 2 || count > 3 ? 0 : 1;
        } else {
            return count == 3 ? 1 : 0;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.48 MB (Beats: 74.66%)

<br>
