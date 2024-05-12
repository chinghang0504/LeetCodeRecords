# [LeetCode Records](../../README.md) - Question 693 Binary Number with Alternating Bits

### Attempt 1: Check the previous last bit
```java
class Solution {
    public boolean hasAlternatingBits(int n) {
        int prevLastBit = (n & 1);
        n >>>= 1;
        
        while (n > 0) {
            int lastBit = (n & 1);
            if (prevLastBit == lastBit) {
                return false;
            }

            prevLastBit = lastBit;
            n >>>= 1;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.44 MB (Beats: 34.11%)

<br>
