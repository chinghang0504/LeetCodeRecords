# [LeetCode Records](../../README.md) - Question 3125 Maximum Number That Makes Result of Bitwise AND Zero

### Attempt 1: Get the first position of binary 1
```java
class Solution {
    public long maxNumber(long n) {
        int count = 0;
        while (n > 0) {
            count++;
            n >>>= 1;
        }

        long val = 1;
        for (int i = 0; i < count - 1; i++) {
            val <<= 1;
        }
        return val - 1;
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 43.88 MB (Beats: 33.33%)

<br>
