# [LeetCode Records](../../README.md) - Question 1009 Complement of Base 10 Integer

### Attempt 1: Count the number of bits first
```java
class Solution {
    public int bitwiseComplement(int n) {
        if (n == 0) {
            return 1;
        }

        int bitCount = 0;
        for (int i = n; i > 0; i >>>= 1) {
            bitCount++;
        }

        n = ~n;
        int moveCount = 32 - bitCount;
        for (int i = 0; i < moveCount; i++) {
            n <<= 1;
        }
        for (int i = 0; i < moveCount; i++) {
            n >>>= 1;
        }

        return n;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.24 MB (Beats: 58.95%)

<br>
