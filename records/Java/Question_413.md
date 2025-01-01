# [LeetCode Records](../../README.md) - Question 413 Arithmetic Slices

### Attempt 1: Use sliding window algorithm
```java
class Solution {
    public int numberOfArithmeticSlices(int[] nums) {
        if (nums.length < 3) {
            return 0;
        }

        int count = 0;
        int startIndex = 0;
        int diff = nums[1] - nums[0];
        for (int i = 2; i < nums.length; i++) {
            int nextDiff = nums[i] - nums[i - 1];
            if (diff == nextDiff) {
                count += i - startIndex - 1;
            } else {
                diff = nextDiff;
                startIndex = i - 1;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.63 MB (Beats: 32.68%)

<br>
