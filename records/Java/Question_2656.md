# [LeetCode Records](../../README.md) - Question 2656 Maximum Sum With Exactly K Elements

### Attempt 1: Find the maximum integer first
```java
class Solution {
    public int maximizeSum(int[] nums, int k) {
        int max = nums[0];
        for (int i = 1; i < nums.length; i++) {
            max = Math.max(max, nums[i]);
        }

        return max * k + (k - 1) * k / 2;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.85 MB (Beats: 41.44%)

<br>
