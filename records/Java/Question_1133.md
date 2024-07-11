# [LeetCode Records](../../README.md) - Question 1133 Largest Unique Number

### Attempt 1: Use Arrays.sort() and a loop
```java
class Solution {
    public int largestUniqueNumber(int[] nums) {
        Arrays.sort(nums);

        int currMax = nums[nums.length - 1];
        boolean isRepeated = false;
        for (int i = nums.length - 2; i >= 0; i--) {
            if (!isRepeated && nums[i] != currMax) {
                return currMax;
            } else if (nums[i] != currMax) {
                isRepeated = false;
                currMax = nums[i];
            } else {
                isRepeated = true;
            }
        }
        if (!isRepeated) {
            return currMax;
        }

        return -1;
    }
}
```
- Runtime: 2 ms (Beats: 88.62%)
- Memory: 42.09 MB (Beats: 97.41%)

<br>
