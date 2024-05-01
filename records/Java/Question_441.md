# [LeetCode Records](../../README.md) - Question 441 Arranging Coins

### Attempt 1: 
```java
class Solution {
    public int arrangeCoins(int n) {
        int count = 0;

        while (n > 0) {
            n -= ++count;
        }

        return n == 0 ? count : count - 1;
    }
}
```
- Runtime: 5 ms (Beats: 51.41%)
- Memory: 40.84 MB (Beats: 52.16%)

<br>
