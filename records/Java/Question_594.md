# [LeetCode Records](../../README.md) - Question 594 Longest Harmonious Subsequence

### Attempt 1: Use Arrays.sort() and count all the numbers
```java
class Solution {
    public int findLHS(int[] nums) {
        Arrays.sort(nums);

        int target = nums[0];
        int count = 1;
        int i = 1;
        while (i < nums.length && nums[i] == target) {
            i++;
            count++;
        }
        if (i == nums.length) {
            return 0;
        }

        int maxCount = 0;
        while (i < nums.length) {
            int nextTarget = nums[i];
            int nextCount = 1;
            
            i++;
            while (i < nums.length && nums[i] == nextTarget) {
                i++;
                nextCount++;
            }

            if (nextTarget - 1 == target) {
                maxCount = Math.max(maxCount, count + nextCount);
            }

            target = nextTarget;
            count = nextCount;
        }

        return maxCount;
    }
}
```
- Runtime: 12 ms (Beats: 99.76%)
- Memory: 45.76 MB (Beats: 26.52%)

<br>
