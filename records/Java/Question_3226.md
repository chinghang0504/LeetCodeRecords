# [LeetCode Records](../../README.md) - Question 3226 Number of Bit Changes to Make Two Integers Equal

### Attempt 1: Use a loop
```java
class Solution {
    public int minChanges(int n, int k) {
        int count = 0;

        for (int i = 0; i < 32; i++) {
            int val1 = n & 1;
            int val2 = k & 1;

            if (val1 == 1 && val2 == 0) {
                count++;
            } else if (val1 == 0 && val2 == 1) {
                return -1;
            }

            n >>>= 1;
            k >>>= 1;
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.18 MB (Beats: 100.00%)

<br>
