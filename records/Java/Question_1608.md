# [LeetCode Records](../../README.md) - Question 1608 Special Array With X Elements Greater Than or Equal X

### Attempt 1: Use Arrays.sort() and a loop
```java
class Solution {
    public int specialArray(int[] nums) {
        Arrays.sort(nums);

        if (nums[0] >= nums.length) {
            return nums.length;
        }

        int x = nums.length - 1;
        for (int i = 1; i < nums.length; i++, x--) {
            if (nums[i] >= x && nums[i - 1] < x) {
                return x;
            }
        }

        return -1;
    }
}
```
- Runtime: 2 ms (Beats: 57.90%)
- Memory: 41.21 MB (Beats: 37.54%)

<br>
