# [LeetCode Records](../../README.md) - Question 794 Valid Tic-Tac-Toe State

### Attempt 1: Count the number of 'X' and 'O' characters
```java
class Solution {
    public boolean validTicTacToe(String[] board) {
        int firstCount = 0;
        int secondCount = 0;
        char[][] gameBoard = new char[3][3];
        for (int i = 0; i < 3; i++) {
            char[] arr = board[i].toCharArray();

            for (int j = 0; j < 3; j++) {
                gameBoard[i][j] = arr[j];
                if (arr[j] == 'X') {
                    firstCount++;
                } else if (arr[j] == 'O') {
                    secondCount++;
                }
            }
        }

        if (secondCount > firstCount || Math.abs(firstCount - secondCount) > 1) {
            return false;
        }

        boolean firstWin = false;
        boolean secondWin = false;
        for (int j = 0; j < 3; j++) {
            if (gameBoard[0][j] == gameBoard[1][j] && gameBoard[1][j] == gameBoard[2][j]) {
                if (gameBoard[0][j] == 'X') {
                    firstWin = true;
                } else if (gameBoard[0][j] == 'O') {
                    secondWin = true;
                }
            }
        }
        for (int i = 0; i < 3; i++) {
            if (gameBoard[i][0] == gameBoard[i][1] && gameBoard[i][1] == gameBoard[i][2]) {
                if (gameBoard[i][0] == 'X') {
                    firstWin = true;
                } else if (gameBoard[i][0] == 'O') {
                    secondWin = true;
                }
            }
        }
        if (gameBoard[0][0] == gameBoard[1][1] && gameBoard[1][1] == gameBoard[2][2]) {
            if (gameBoard[0][0] == 'X') {
                firstWin = true;
            } else if (gameBoard[0][0] == 'O') {
                secondWin = true;
            }
        }
        if (gameBoard[0][2] == gameBoard[1][1] && gameBoard[1][1] == gameBoard[2][0]) {
            if (gameBoard[0][2] == 'X') {
                firstWin = true;
            } else if (gameBoard[0][2] == 'O') {
                secondWin = true;
            }
        }

        if (firstWin && secondWin) {
            return false;
        } else if (firstWin) {
            return firstCount > secondCount;
        } else if (secondWin) {
            return firstCount == secondCount;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.10 MB (Beats: 31.90%)

<br>
