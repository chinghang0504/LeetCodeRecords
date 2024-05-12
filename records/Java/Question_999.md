# [LeetCode Records](../../README.md) - Question 999 Available Captures for Rook

### Attempt 1: Find the position of rook first
```java
class Solution {
    public int numRookCaptures(char[][] board) {
        int row = 0;
        int col = 0;
        find: for (int i = 0; i < 8; i++) {
            for (int j = 0; j < 8; j++) {
                if (board[i][j] == 'R') {
                    row = i;
                    col = j;
                    break find;
                }
            }
        }

        int count = 0;
        for (int i = row - 1; i >= 0; i--) {
            char target = board[i][col];
            if (target == 'B') {
                break;
            } else if (target == 'p') {
                count++;
                break;
            }
        }
        for (int i = row + 1; i < 8; i++) {
            char target = board[i][col];
            if (target == 'B') {
                break;
            } else if (target == 'p') {
                count++;
                break;
            }
        }
        for (int j = col - 1; j >= 0; j--) {
            char target = board[row][j];
            if (target == 'B') {
                break;
            } else if (target == 'p') {
                count++;
                break;
            }
        }
        for (int j = col + 1; j < 8; j++) {
            char target = board[row][j];
            if (target == 'B') {
                break;
            } else if (target == 'p') {
                count++;
                break;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.87 MB (Beats: 46.15%)

<br>
