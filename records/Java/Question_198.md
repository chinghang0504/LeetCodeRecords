# [LeetCode Records](../../README.md) - Question 198 House Robber

### Attempt 1: Track two current maximum numbers
```java
class Solution {
    public int rob(int[] nums) {
        if (nums.length == 1) {
            return nums[0];
        }

        int max1 = nums[0];
        int max2 = nums[1];

        for (int i = 2; i < nums.length; i++) {
            int nextMax1 = Math.max(max1, max2);
            int nextMax2 = max1 + nums[i];
            max1 = nextMax1;
            max2 = nextMax2;
        }

        return Math.max(max1, max2);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.88 MB (Beats: 62.65%)

<br>
