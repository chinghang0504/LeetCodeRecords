# [LeetCode Records](../README.md) - Question 190 Reverse Bits

### Attempt 1: 
```java
public class Solution {
    public int reverseBits(int n) {
        int result = 0;

        for (int i = 0; i < 31; i++) {
            result += (n & 0x1);
            n >>>= 1;
            result <<= 1;
        }
        result += (n & 0x1);

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.64 MB (Beats: 55.31%)

<br>
