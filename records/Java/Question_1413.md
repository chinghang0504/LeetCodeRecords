# [LeetCode Records](../../README.md) - Question 1413 Minimum Value to Get Positive Step by Step Sum

### Attempt 1: Record the current sum and the minimum current sum
```java
class Solution {
    public int minStartValue(int[] nums) {
        int startValue = 0;
        int currSum = startValue + nums[0];
        int minCurrSum = currSum;

        for (int i = 1; i < nums.length; i++) {
            currSum += nums[i];
            minCurrSum = Math.min(minCurrSum, currSum);
        }

        return minCurrSum < 1 ? 1 - minCurrSum : 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.81 MB (Beats: 57.28%)

<br>
