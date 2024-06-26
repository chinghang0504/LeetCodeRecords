# [LeetCode Records](../../README.md) - Question 1812 Determine Color of a Chessboard Square

### Attempt 1: 
```java
class Solution {
    public boolean squareIsWhite(String coordinates) {
        int col = coordinates.charAt(0) - 'a' + 1;
        int row = Integer.valueOf(coordinates.charAt(1));

        if ((row % 2 == 0 && col % 2 == 0) || (row % 2 == 1 && col % 2 == 1)) {
            return false;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.19 MB (Beats: 52.38%)

<br>
