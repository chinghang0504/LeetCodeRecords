# [LeetCode Records](../README.md) - Question 419 Battleships in a Board

### Attempt 1: Remove the battleship from the board after it is found
```java
class Solution {
    public int countBattleships(char[][] board) {
        int count = 0;
        int m = board.length;
        int n = board[0].length;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (board[i][j] == 'X') {
                    count++;
                    removeBattleship(board, m, n, i, j);
                }
            }
        }

        return count;
    }

    private void removeBattleship(char[][] board, int m, int n, int start_i, int start_j) {
        for (int i = start_i + 1; i < m; i++) {
            if (board[i][start_j] == 'X') {
                board[i][start_j] = '.';
            } else {
                break;
            }
        }
        for (int j = start_j + 1; j < n; j++) {
            if (board[start_i][j] == 'X') {
                board[start_i][j] = '.';
            } else {
                break;
            }
        }
        board[start_i][start_j] = '.';
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.88 MB (Beats: 10.08%)

<br>
