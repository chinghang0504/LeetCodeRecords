# [LeetCode Records](../../README.md) - Question 1275 Find Winner on a Tic Tac Toe Game

### Attempt 1: Use three helper functions to check if the winner is in a row, a col, or a diagonal
```java
class Solution {
    
    public String tictactoe(int[][] moves) {
        char[][] board = { { '1', '2', '3' }, { '4', '5', '6' }, { '7', '8', '9' } };

        for (int i = 0; i < moves.length; i++) {
            int[] move = moves[i];
            board[move[0]][move[1]] = i % 2 == 0 ? 'X' : '0';
        }

        for (int i = 0; i < 3; i++) {
            if (isWinnerInRow(board, i)) {
                return board[i][0] == 'X' ? "A" : "B";
            }
        }
        for (int i = 0; i < 3; i++) {
            if (isWinnerInCol(board, i)) {
                return board[0][i] == 'X' ? "A" : "B";
            }
        }
        for (int i = 0; i < 2; i++) {
            if (isWinnerInDiagonal(board, i)) {
                return board[1][1] == 'X' ? "A" : "B";
            }
        }

        return moves.length == 9 ? "Draw" : "Pending";
    }

    private boolean isWinnerInRow(char[][] board, int row) {
        return board[row][0] == board[row][1] && board[row][0] == board[row][2];
    }

    private boolean isWinnerInCol(char[][] board, int col) {
        return board[0][col] == board[1][col] && board[0][col] == board[2][col];
    }

    private boolean isWinnerInDiagonal(char[][] board, int diagonal) {
        if (diagonal == 0) {
            return board[0][0] == board[1][1] && board[0][0] == board[2][2];
        } else {
            return board[0][2] == board[1][1] && board[0][2] == board[2][0];
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.92 MB (Beats: 78.32%)

<br>
