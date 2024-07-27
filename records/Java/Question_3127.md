# [LeetCode Records](../../README.md) - Question 3127 Make a Square with the Same Color

### Attempt 1: Count the number of same colors in 2x2
```java
class Solution {
    public boolean canMakeSquare(char[][] grid) {
        for (int i = 0; i < 2; i++) {
            for (int j = 0; j < 2; j++) {
                int countWhite = 0;
                int countBlack = 0;

                for (int x = 0; x < 2; x++) {
                    for (int y = 0; y < 2; y++) {
                        if (grid[i + x][j + y] == 'W') {
                            countWhite++;
                        } else {
                            countBlack++;
                        }
                    }
                }

                if (countWhite >= 3 || countBlack >= 3) {
                    return true;
                }
            }
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.37 MB (Beats: 92.06%)

<br>
