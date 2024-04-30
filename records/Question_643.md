# [LeetCode Records](../README.md) - Question 643 Maximum Average Subarray I

### Attempt 1: 
```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {
        int sum = 0;
        for (int i = 0; i < k; i++) {
            sum += nums[i];
        }
        int maxSum = sum;

        for (int i = k; i < nums.length; i++) {
            sum = sum - nums[i - k] + nums[i];
            if (sum > maxSum) {
                maxSum = sum;
            }
        }

        return (double)maxSum / k;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 55.15 MB (Beats: 92.09%)

<br>
