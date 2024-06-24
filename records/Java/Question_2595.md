# [LeetCode Records](../../README.md) - Question 2595 Number of Even and Odd Bits

### Attempt 1: Use a loop
```java
class Solution {
    public int[] evenOddBit(int n) {
        int eventCount = 0;
        int oddCount = 0;

        int currIndex = 0;
        while (n > 0) {
            if ((n & 1) != 0) {
                if (currIndex % 2 == 0) {
                    eventCount++;
                } else {
                    oddCount++;
                }
            }

            n >>>= 1;
            currIndex++;
        }

        return new int[]{eventCount, oddCount};
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.12 MB (Beats: 71.39%)

<br>
