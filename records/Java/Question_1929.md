# [LeetCode Records](../../README.md) - Question 1929 Concatenation of Array

### Attempt 1: Use a loop
```java
class Solution {
    public int[] getConcatenation(int[] nums) {
        int[] ans = new int[nums.length * 2];

        for (int i = 0; i < nums.length; i++) {
            ans[i] = nums[i];
            ans[i + nums.length] = nums[i];
        }

        return ans;
    }
}
```
- Runtime: 1 ms (Beats: 96.28%)
- Memory: 44.45 MB (Beats: 97.71%)

<br>
