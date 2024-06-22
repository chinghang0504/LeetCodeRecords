# [LeetCode Records](../../README.md) - Question 1920 Build Array from Permutation

### Attempt 1: Use a loop
```java
class Solution {
    public int[] buildArray(int[] nums) {
        int[] ans = new int[nums.length];

        for (int i = 0; i < nums.length; i++) {
            ans[i] = nums[nums[i]];
        }

        return ans;
    }
}
```
- Runtime: 1 ms (Beats: 98.71%)
- Memory: 44.95 MB (Beats: 81.38%)

<br>
