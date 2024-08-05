# [LeetCode Records](../../README.md) - Question 674 Longest Continuous Increasing Subsequence

### Attempt 1: Track the current and the maximum counts
```java
class Solution {
    public int findLengthOfLCIS(int[] nums) {
        int maxCount = 1;
        int count = 1;

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > nums[i - 1]) {
                count++;

                maxCount = Math.max(maxCount, count);
            } else {
                count = 1;
            }
        }

        return maxCount;
    }
}
```
- Runtime: 1 ms (Beats: 99.69%)
- Memory: 44.33 MB (Beats: 50.24%)

<br>
