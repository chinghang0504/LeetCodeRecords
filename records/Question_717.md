# [LeetCode Records](../README.md) - Question 717 1-bit and 2-bit Characters

### Attempt 1: 
```java
class Solution {
    public boolean isOneBitCharacter(int[] bits) {
        int i = 0;
        while (i < bits.length - 1) {
            if (bits[i] == 0) {
                i++;
            } else {
                i += 2;
            }
        }

        return i == bits.length - 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.48 MB (Beats: 55.96%)

<br>
