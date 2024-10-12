# [LeetCode Records](../../README.md) - Question 2219 Maximum Sum Score of Array

### Attempt 1: Track the left sum and the right sum
```java
class Solution {
    public long maximumSumScore(int[] nums) {
        long leftSum = 0;
        long rightSum = 0;
        for (int num : nums) {
            rightSum += num;
        }

        long maxScore = Integer.MIN_VALUE;
        for (int i = 0; i < nums.length; i++) {
            leftSum += nums[i];

            long score = Math.max(leftSum, rightSum);
            maxScore = Math.max(maxScore, score);

            rightSum -= nums[i];
        }

        return maxScore;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 56.46 MB (Beats: 69.09%)

<br>
