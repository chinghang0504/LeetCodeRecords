# [LeetCode Records](../../README.md) - Question 3360 Stone Removal Game

### Attempt 1: Track the player's turn
```java
class Solution {
    public boolean canAliceWin(int n) {
        boolean isAliceTurn = true;
        int curr = 10;

        while (n >= curr) {
            n -= curr;
            curr--;
            isAliceTurn = !isAliceTurn;
        }

        return !isAliceTurn;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.09 MB (Beats: 100.00%)

<br>
