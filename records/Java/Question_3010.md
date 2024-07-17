# [LeetCode Records](../../README.md) - Question 3010 Divide an Array Into Subarrays With Minimum Cost I

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int minimumCost(int[] nums) {
        Arrays.sort(nums, 1, nums.length);

        return nums[0] + nums[1] + nums[2];
    }
}
```
- Runtime: 2 ms (Beats: 33.33%)
- Memory: 43.94 MB (Beats: 45.45%)

<br>
