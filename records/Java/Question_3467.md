# [LeetCode Records](../../README.md) - Question 3467 Transform Array by Parity

### Attempt 1: Track the current index for zeros
```java
class Solution {
    public int[] transformArray(int[] nums) {
        int startIndex = 0;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] % 2 == 0) {
                nums[startIndex++] = 0;
            }
        }

        for (int i = startIndex; i < nums.length; i++) {
            nums[i] = 1;
        }

        return nums;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.89 MB (Beats: 90.66%)

<br>
