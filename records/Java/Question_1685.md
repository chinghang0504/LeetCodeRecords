# [LeetCode Records](../../README.md) - Question 1685 Sum of Absolute Differences in a Sorted Array

### Attempt 1: Calculate the cumulative sum
```java
class Solution {
    public int[] getSumAbsoluteDifferences(int[] nums) {
        int[] cumsums = new int[nums.length];
        int cumsum = 0;
        for (int i = 0; i < nums.length; i++) {
            cumsum += nums[i];
            cumsums[i] = cumsum;
        }

        int[] ans = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            int sum = 0;

            if (i - 1 >= 0) {
                sum += nums[i] * i - cumsums[i - 1];
            }
            if (i + 1 < nums.length) {
                sum += (cumsums[nums.length - 1] - cumsums[i]) - nums[i] * (nums.length - i - 1);
            }

            ans[i] = sum;
        }

        return ans;
    }
}
```
- Runtime: 5 ms (Beats: 39.57%)
- Memory: 58.02 MB (Beats: 36.45%)

<br>
