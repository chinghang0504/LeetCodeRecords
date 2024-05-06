# [LeetCode Records](../../README.md) - Question 868 Binary Gap

### Attempt 1: Record the last index of the one
```java
class Solution {
    public int binaryGap(int n) {
        int currIndex = 0;
        while ((n & 1) != 1) {
            n >>>= 1;
            currIndex++;
        }

        int lastOneIndex = currIndex;
        int max = 0;
        while (n > 0) {
            if ((n & 1) == 1) {
                max = Math.max(max, currIndex - lastOneIndex);
                lastOneIndex = currIndex;
            }

            n >>>= 1;
            currIndex++;
        }

        return max;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.27 MB (Beats: 72.86%)

<br>
