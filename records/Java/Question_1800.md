# [LeetCode Records](../../README.md) - Question 1800 Maximum Ascending Subarray Sum

### Attempt 1: Use a loop
```java
class Solution {
    public int maxAscendingSum(int[] nums) {
        int currSum = nums[0];
        int maxSum = 0;

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > nums[i - 1]) {
                currSum += nums[i];
            } else {
                maxSum = Math.max(maxSum, currSum);
                currSum = nums[i];
            }
        }
        maxSum = Math.max(maxSum, currSum);

        return maxSum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.22 MB (Beats: 30.19%)

<br>
