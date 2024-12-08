# [LeetCode Records](../../README.md) - Question 3379 Transformed Array

### Attempt 1: Calculate the corresponding indices
```java
class Solution {
    public int[] constructTransformedArray(int[] nums) {
        int[] ans = new int[nums.length];

        for (int i = 0; i < nums.length; i++) {
            int index = i + nums[i] % nums.length;
            if (index >= nums.length) {
                index %= nums.length;
            } else if (index < 0) {
                index += nums.length;
            }

            ans[i] = nums[index];
        }

        return ans;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.72 MB (Beats: 100.00%)

<br>
