# [LeetCode Records](../../README.md) - Question 2293 Min Max Game

### Attempt 1: Use recursion
```java
class Solution {
    public int minMaxGame(int[] nums) {
        if (nums.length == 1) {
            return nums[0];
        }

        int n = nums.length / 2;
        int[] answer = new int[n];
        for (int i = 0; i < n; i++) {
            answer[i] = i % 2 == 0 ? Math.min(nums[i * 2], nums[i * 2 + 1]) : Math.max(nums[i * 2], nums[i * 2 + 1]);
        }

        return minMaxGame(answer);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.62 MB (Beats: 16.82%)

<br>
