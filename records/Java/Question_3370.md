# [LeetCode Records](../../README.md) - Question 3370 Smallest Number With All Set Bits

### Attempt 1: Use a while loop to generate the smallest number
```java
class Solution {
    public int smallestNumber(int n) {
        int ans = 0;
        while (n > 0) {
            n >>>= 1;
            ans = (ans << 1) + 1;
        }

        return ans;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.45 MB (Beats: 100.00%)

<br>
