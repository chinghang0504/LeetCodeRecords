# [LeetCode Records](../../README.md) - Question 360 Sort Transformed Array

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int[] sortTransformedArray(int[] nums, int a, int b, int c) {
        for (int i = 0; i < nums.length; i++) {
            nums[i] = a * nums[i] * nums[i] + b * nums[i] + c;
        }

        Arrays.sort(nums);
        
        return nums;
    }
}
```
- Runtime: 2 ms (Beats: 40.67%)
- Memory: 42.33 MB (Beats: 92.34%)

<br>
