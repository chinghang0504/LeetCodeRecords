# [LeetCode Records](../../README.md) - Question 53 Maximum Subarray

### Attempt 1: Compare the current sum and the next number
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSum = nums[0];
        int currSum = nums[0];

        int i = 1;
        while (i < nums.length) {
            if (currSum + nums[i] > nums[i]) {
                currSum += nums[i];
            } else {
                currSum = nums[i];
            }

            maxSum = Math.max(maxSum, currSum);
            i++;
        }

        return maxSum;
    }
}
```
- Runtime: 1 ms (Beats: 99.45%)
- Memory: 56.41 MB (Beats: 96.67%)

<br>
