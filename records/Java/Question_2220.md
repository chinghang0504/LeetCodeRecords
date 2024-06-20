# [LeetCode Records](../../README.md) - Question 2220 Minimum Bit Flips to Convert Number

### Attempt 1: Use an int[] to save the digits
```java
class Solution {
    public int minBitFlips(int start, int goal) {
        int[] goalDigits = new int[32];

        for (int i = 0; i < 32; i++) {
            goalDigits[i] = (goal & 0x1);
            goal >>>= 1;
        }

        int count = 0;

        for (int i = 0; i < 32; i++) {
            if (goalDigits[i] != (start & 0x1)) {
                count++;
            }
            start >>>= 1;
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.61 MB (Beats: 18.43%)

<br>
