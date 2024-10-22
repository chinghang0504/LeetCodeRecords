# [LeetCode Records](../../README.md) - Question 189 Rotate Array

### Attempt 1: Create a new int[] for cache
```java
class Solution {
    public void rotate(int[] nums, int k) {
        k %= nums.length;
        if (k == 0) {
            return;
        }

        int[] ans = new int[nums.length];
        int ansIndex = 0;
        int startIndex = nums.length - k;
        for (int i = startIndex; i < nums.length; i++) {
            ans[ansIndex] = nums[i];
            ansIndex++;
        }
        for (int i = 0; i < startIndex; i++) {
            ans[ansIndex] = nums[i];
            ansIndex++;
        }

        for (int i = 0; i < nums.length; i++) {
            nums[i] = ans[i];
        }
    }
}
```
- Runtime: 1 ms (Beats: 49.93%)
- Memory: 57.28 MB (Beats: 61.98%)

<br>
