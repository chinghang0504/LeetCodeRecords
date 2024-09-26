# [LeetCode Records](../../README.md) - Question 2044 Count Number of Maximum Bitwise-OR Subsets

### Attempt 1: Calculate the maximum or value first
```java
class Solution {
    public int countMaxOrSubsets(int[] nums) {
        int max = 0;
        for (int num : nums) {
            max |= num;
        }

        int count = getCount(nums, max, 0, 0);

        return count;
    }

    private int getCount(int[] nums, int max, int prevVal, int startIndex) {
        if (startIndex >= nums.length) {
            return 0;
        }

        int count = 0;
        for (int i = startIndex; i < nums.length; i++) {
            int val = prevVal | nums[i];
            if (val == max) {
                count += Math.pow(2, nums.length - i - 1);
            } else {
                count += getCount(nums, max, val, i + 1);
            }
        }

        return count;
    }
}
```
- Runtime: 3 ms (Beats: 99.00%)
- Memory: 40.79 MB (Beats: 83.67%)

<br>
