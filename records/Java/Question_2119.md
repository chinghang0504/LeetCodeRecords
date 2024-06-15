# [LeetCode Records](../../README.md) - Question 2119 A Number After a Double Reversal

### Attempt 1: Check the rightmost zero
```java
class Solution {
    public boolean isSameAfterReversals(int num) {
        if (num == 0) {
            return true;
        }

        return num % 10 != 0;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 39.90 MB (Beats: 94.80%)

<br>
