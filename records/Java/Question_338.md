# [LeetCode Records](../../README.md) - Question 338 Counting Bits

### Attempt 1: Count every number
```java
class Solution {
    public int[] countBits(int n) {
        int[] result = new int[n + 1];

        for (int i = 0; i < n + 1; i++) {
            countBits(i, result);
        }

        return result;
    }

    private void countBits(int n, int[] result) {
        int count = 0;
        int curr = n;
        for (int i = 0; i < 31; i++) {
            if ((curr & 0x1) == 1) {
                count++;
            }
            curr >>= 1;
        }
        result[n] = count;
    }
}
```
- Runtime: 8 ms (Beats: 16.97%)
- Memory: 46.50 MB (Beats: 48.36%)

<br>
