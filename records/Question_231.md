# [LeetCode Records](../README.md) - Question 231 Power of Two

### Attempt 1: Remove all the trailing zeros first
```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        if (n <= 0) {
            return false;
        }

        int i = 0;
        for (; i < 31 && (n & 0x1) == 0; i++) {
            n >>= 1;
        }

        return n == 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.51 MB (Beats: 78.98%)

<br>
