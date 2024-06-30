# [LeetCode Records](../../README.md) - Question 1913 Maximum Product Difference Between Two Pairs

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int maxProductDifference(int[] nums) {
        Arrays.sort(nums);

        return nums[nums.length - 1] * nums[nums.length - 2] - nums[0] * nums[1];
    }
}
```
- Runtime: 7 ms (Beats: 59.21%)
- Memory: 44.88 MB (Beats: 60.39%)

<br>
