# [LeetCode Records](../../README.md) - Question 1464 Maximum Product of Two Elements in an Array

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int maxProduct(int[] nums) {
        Arrays.sort(nums);

        return (nums[nums.length - 1] - 1) * (nums[nums.length - 2] - 1);
    }
}
```
- Runtime: 2 ms (Beats: 63.70%)
- Memory: 42.84 MB (Beats: 24.26%)

<br>
