# [LeetCode Records](../../README.md) - Question 348 Design Tic-Tac-Toe

### Attempt 1: 
```java
class TicTacToe {

    private int[][] board;
    private int n;

    public TicTacToe(int n) {
        this.board = new int[n][n];
        this.n = n;
    }
    
    public int move(int row, int col, int player) {
        board[row][col] = player;

        if (checkBoard(row, col, player)) {
            return player;
        }

        return 0;
    }

    private boolean checkBoard(int row, int col, int player) {
        boolean isWon = true;

        // Check the column
        for (int i = 0; i < n; i++) {
            if (board[i][col] != player) {
                isWon = false;
                break;
            }
        }
        if (isWon) {
            return true;
        }

        // Check the row
        isWon = true;
        for (int j = 0; j < n; j++) {
            if (board[row][j] != player) {
                isWon = false;
                break;
            }
        }
        if (isWon) {
            return true;
        }

        // Check the cross
        if (row != col && row != n - 1 - col) {
            return false;
        }

        isWon = true;
        for (int i = 0; i < n; i++) {
            if (board[i][i] != player) {
                isWon = false;
                break;
            }
        }
        if (isWon) {
            return true;
        }

        isWon = true;
        for (int i = 0; i < n; i++) {
            if (board[i][n - 1 - i] != player) {
                isWon = false;
                break;
            }
        }
        if (isWon) {
            return true;
        }

        return false;
    }
}
```
- Runtime: 3 ms (Beats: 99.85%)
- Memory: 45.59 MB (Beats: 39.32%)

<br>
