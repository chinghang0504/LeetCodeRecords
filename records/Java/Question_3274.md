# [LeetCode Records](../../README.md) - Question 3274 Check if Two Chessboard Squares Have the Same Color

### Attempt 1: Check the parities of horizontal and vertical positions
```java
class Solution {
    public boolean checkTwoChessboards(String coordinate1, String coordinate2) {
        return isBlack(coordinate1) == isBlack(coordinate2);
    }

    private boolean isBlack(String coordinate) {
        char ch1 = coordinate.charAt(0);
        char ch2 = coordinate.charAt(1);
        return (ch1 - 'a') % 2 == (ch2 - '1') % 2;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.90 MB (Beats: 100.00%)

<br>
