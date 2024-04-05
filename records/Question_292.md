# [LeetCode Records](../README.md) - Question 292 Nim Game

### Attempt 1: 
```java
class Solution {
    public boolean canWinNim(int n) {
        if (n == 1 || n == 2 || n == 3) {
            return true;
        }

        return n % 4 != 0;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.02 MB (Beats: 77.18%)

<br>
