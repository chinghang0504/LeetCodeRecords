# [LeetCode Records](../../README.md) - Question 3423 Maximum Difference Between Adjacent Elements in a Circular Array

### Attempt 1: Use a for loop to compare with the previous number
```java
class Solution {
    public int maxAdjacentDistance(int[] nums) {
        int maxDiff = 0;

        for (int i = 1; i < nums.length; i++) {
            maxDiff = Math.max(maxDiff, Math.abs(nums[i] - nums[i - 1]));
        }
        maxDiff = Math.max(maxDiff, Math.abs(nums[0] - nums[nums.length - 1]));

        return maxDiff;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 43.58 MB (Beats: 100.00%)

<br>
