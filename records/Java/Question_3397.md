# [LeetCode Records](../../README.md) - Question 3397 Maximum Number of Distinct Elements After Operations

### Attempt 1: Track the minimum number
```java
class Solution {
    public int maxDistinctElements(int[] nums, int k) {
        Arrays.sort(nums);

        int count = 1;
        int nextMinNum = nums[0] - k + 1;
        for (int i = 1; i < nums.length; i++) {
            int lowerTarget = nums[i] - k;
            int upperTarget = nums[i] + k;
            if (lowerTarget <= nextMinNum && nextMinNum <= upperTarget) {
                nextMinNum++;
                count++;
            } else if (lowerTarget >= nextMinNum) {
                nextMinNum = lowerTarget + 1;
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 17 ms (Beats: 100.00%)
- Memory: 65.02 MB (Beats: 100.00%)

<br>
