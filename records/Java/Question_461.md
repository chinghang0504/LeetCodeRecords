# [LeetCode Records](../../README.md) - Question 461 Hamming Distance

### Attempt 1: 
```java
class Solution {
    public int hammingDistance(int x, int y) {
        int count = 0;

        for (int i = 0; i < 31; i++) {
            if ((x & 0x1) != (y & 0x1)) {
                count++;
            }
            x >>>= 1;
            y >>>= 1;
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.47 MB (Beats: 38.28%)

<br>
