# [LeetCode Records](../../README.md) - Question 2090 K Radius Subarray Averages

### Attempt 1: Track the current sum
```java
class Solution {
    public int[] getAverages(int[] nums, int k) {
        int len = k + k + 1;
        if (nums.length < len) {
            int[] ans = new int[nums.length];
            Arrays.fill(ans, -1);
            return ans;
        }

        int[] ans = new int[nums.length];
        int ansIndex = 0;
        for (; ansIndex < k; ansIndex++) {
            ans[ansIndex] = -1;
        }

        long currSum = 0;
        for (int i = 0; i < len; i++) {
            currSum += nums[i];
        }

        ans[ansIndex] = (int)(currSum / len);
        ansIndex++;

        for (int endIndex = len; endIndex < nums.length; endIndex++) {
            currSum = currSum + nums[endIndex] - nums[endIndex - len];
            ans[ansIndex] = (int)(currSum / len);
            ansIndex++;
        }

        for (; ansIndex < nums.length; ansIndex++) {
            ans[ansIndex] = -1;
        }

        return ans;
    }
}
```
- Runtime: 4 ms (Beats: 100.00%)
- Memory: 64.59 MB (Beats: 27.08%)

<br>
