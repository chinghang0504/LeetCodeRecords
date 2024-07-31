# [LeetCode Records](../../README.md) - Question 2239 Find Closest Number to Zero

### Attempt 1: Use a for loop to find the answer
```java
class Solution {
    public int findClosestNumber(int[] nums) {
        int minDiff = Integer.MAX_VALUE;
        int answer = 0;

        for (int i = 0; i < nums.length; i++) {
            int diff = Math.abs(nums[i]);
            if (diff < minDiff) {
                minDiff = diff;
                answer = nums[i];
            } else if (diff == minDiff) {
                answer = Math.max(answer, nums[i]);
            }
        }

        return answer;
    }
}
```
- Runtime: 2 ms (Beats: 90.24%)
- Memory: 44.72 MB (Beats: 60.97%)

<br>
