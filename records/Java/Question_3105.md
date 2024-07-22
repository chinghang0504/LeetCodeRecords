# [LeetCode Records](../../README.md) - Question 3105 Longest Strictly Increasing or Strictly Decreasing Subarray

### Attempt 1: Record the maximum and current length
```java
class Solution {
    public int longestMonotonicSubarray(int[] nums) {
        int maxLength = 1;
        int currLength = 1;
        boolean isIncreased = true;

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > nums[i - 1]) {
                if (isIncreased) {
                    currLength++;
                } else {
                    isIncreased = true;
                    currLength = 2;
                }
                maxLength = Math.max(maxLength, currLength);
            } else if (nums[i] == nums[i - 1]) {
                currLength = 1;
            } else {
                if (isIncreased) {
                    isIncreased = false;
                    currLength = 2;
                } else {
                    currLength++;
                }
                maxLength = Math.max(maxLength, currLength);
            }
        }

        return maxLength;
    }
}
```
- Runtime: 1 ms (Beats: 89.21%)
- Memory: 42.51 MB (Beats: 46.68%)

<br>
