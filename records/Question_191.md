# [LeetCode Records](../README.md) - Question 191 Number of 1 Bits

### Attempt 1: Count the last bit
```java
class Solution {
    public int hammingWeight(int n) {
        int count = 0;

        for (int i = 0; i < 32; i++) {
            int val = n & 0x1;
            if (val != 0) {
                count++;
            }
            n >>= 1;
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.91 MB (Beats: 11.20%)

<br>
