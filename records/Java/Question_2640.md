# [LeetCode Records](../../README.md) - Question 2640 Find the Score of All Prefixes of an Array

### Attempt 1: Calculate the maximum number of array first
```java
class Solution {
    public long[] findPrefixScore(int[] nums) {
        int[] maxNums = new int[nums.length];

        int currMax = nums[0];
        for (int i = 0; i < nums.length; i++) {
            currMax = Math.max(currMax, nums[i]);
            maxNums[i] = currMax;
        }

        long[] ans = new long[nums.length];
        long currSum = 0;
        for (int i = 0; i < nums.length; i++) {
            long val = nums[i] + maxNums[i];
            currSum += val;
            ans[i] = currSum;
        }

        return ans;
    }
}
```
- Runtime: 3 ms (Beats: 83.75%)
- Memory: 66.65 MB (Beats: 13.59%)

<br>
