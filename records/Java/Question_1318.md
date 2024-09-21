# [LeetCode Records](../../README.md) - Question 1318 Minimum Flips to Make a OR b Equal to c

### Attempt 1: Convert a or b to binary 1 counts
```java
class Solution {
    public int minFlips(int a, int b, int c) {
        int[] aOrBVal = new int[32];
        int[] cVal = new int[32];
        for (int i = 0; i < 32; i++) {
            aOrBVal[i] = (a & 1) + (b & 1);
            cVal[i] = c & 1;

            a >>>= 1;
            b >>>= 1;
            c >>>= 1;
        }

        int count = 0;
        for (int i = 0; i < 32; i++) {
            if (cVal[i] != aOrBVal[i]) {
                if (cVal[i] == 0) {
                    count += aOrBVal[i];
                } else if (aOrBVal[i] == 0) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.72 MB (Beats: 9.43%)

<br>
